<template>
    <h6>Listado de Digimons</h6>
    <div class="digimon-list">
        <div class="digimon-grid">
            <div class="digimon-item" v-for="item in filteredDigimons" :key="item.name">
                <DigimonItem :digimon="item"/>
            </div>  
        </div>
    </div>
</template>

<style>
    .digimon-grid{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 16px;
    }
</style>

<script>
import DigimonItem from 'src/components/digimon/DigimonItem.vue';


export default {
    name: 'DigimonList',
    components: {
        DigimonItem,
    },
    props: {
        filterLevel: {
            type: String,
            default: null,
        },
        filterName: {
            type: String,
            default: null,
        },
    },
    data() {
        return {
            allDigimons: [],
        }
    },
    mounted() {
        this.fetchDigimons();
    },
    computed: {
        filteredDigimons() {
            // If no filters, return all
            const hasLevel = this.filterLevel && this.filterLevel.toString().trim() !== '';
            const hasName = this.filterName && this.filterName.toString().trim() !== '';
            if (!hasLevel && !hasName) return this.allDigimons;

            return this.allDigimons.filter(d => {
                let ok = true;
                if (hasLevel) {
                    if (!d.level) ok = false;
                    else ok = ok && d.level.toLowerCase() === this.filterLevel.toLowerCase();
                }
                if (hasName) {
                    if (!d.name) ok = false;
                    else ok = ok && d.name.toLowerCase().includes(this.filterName.toLowerCase());
                }
                return ok;
            });
        }
    },
    methods: {
        async fetchDigimons() {
            try {
                const response = await fetch('https://digimon-api.vercel.app/api/digimon');
                const data = await response.json();
                this.allDigimons = data;
            } catch (error) {
                console.error('Error fetching digimons:', error);
            }
        },
    },
}
</script>