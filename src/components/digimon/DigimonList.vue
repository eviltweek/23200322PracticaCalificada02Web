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
            if (!this.filterLevel) return this.allDigimons;
            return this.allDigimons.filter(d => {
                // Some levels may be null or uppercase/lowercase variants; compare case-insensitive
                if (!d.level) return false;
                return d.level.toLowerCase() === this.filterLevel.toLowerCase();
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