<template>
    <q-card class="digimon-card">
    <q-card-section>
        <q-img :src="item.img" alt="Imagn del digimon"/>
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
</script>