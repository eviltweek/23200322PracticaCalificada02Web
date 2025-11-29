<template>
    <q-card class="digimon-card">
    <q-card-section>
        <q-img :src="digimon.img" alt="Imagen del digimon"/>
    </q-card-section>
    <q-card-section>
        <q-card-title>{{ digimon.name }}</q-card-title>
        <div class="text h-6 font-weight-bold">{{ digimon.level }}</div>
        <div class="text-center">
        </div>
    </q-card-section>
    </q-card>
</template>
<style>
    .product-card{
        max-width:300px;
        margin: auto;
    }
    .product-card q-card-section{
        height: 100px;
        overflow:hidden;
    }
</style>

<script>
    export default {
        name: 'DigimonItem',
        props:{
            digimon: {
            type: Object,
            required: true,
            },
        }
    }
</script>