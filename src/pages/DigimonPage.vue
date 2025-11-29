<template>

    <div class="digimon-page">
        <div class="digimon-filter q-ml-md q-mr-xl">
            <DigimonFilter @change-level="selectedLevel = $event" @change-name="selectedName = $event"/>
        </div>

        <div class="digimon-list q-ml-xl q-mr-md">
            <DigimonList :filter-level="selectedLevel" :filter-name="selectedName"/>
        </div>

    </div>   
</template>

<style>
.digimon-page{
    display: flex;
    justify-content: space-between;
}
.digimon-filter{
    width: 25%;
}
.digimon-list{
    width: 75%;
}
</style>

<script>
import DigimonFilter from 'src/components/digimon/DigimonFilter.vue';
import DigimonList from 'src/components/digimon/DigimonList.vue';
export default {
    name: 'DigimonPage',
    components: {
        DigimonFilter,
        DigimonList,
    },
    data() {
        return {
            selectedLevel: null,
            selectedName: null,
        };
    },
}
</script>
