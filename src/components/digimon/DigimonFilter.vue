<template>
    <h6>Filtros</h6>
    <div class="name-filter q-mb-sm">
        <q-input label="Nombre" v-model="nameSelected" clearable/>
    </div>
    <div class="level-filter">
        <q-select label="Nivel" v-model="levelSelected" :options="level" clearable/>
    </div>
</template>
<style></style>
<script>
    export default {
        name: 'DigimonFilter',
        data() {
                return {
                    level: [   
                        'In Training',
                        'Rookie',
                        'Champion',
                        'Ultimate',
                        'Mega',
                        'Fresh',
                    ],
                        levelSelected: null,
                        nameSelected: null,
                }
            },
            watch: {
                levelSelected(newVal) {
                    this.$emit('change-level', newVal);
                },
                nameSelected(newVal) {
                    this.$emit('change-name', newVal);
                }
            },
    }
</script>