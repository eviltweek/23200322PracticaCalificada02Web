<template>
    <h6>Filtros</h6>
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
                }
            },
        watch: {
            levelSelected(newVal) {
                this.$emit('change-level', newVal);
            }
        },
    }
</script>