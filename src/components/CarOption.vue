<template>
    <h2>Car - Option APi</h2>
    <p>Marca: {{ brand }}</p>
    <p>Modelo: {{ model }}</p>
    <p>Power: {{ power }}</p>

    <button @click="upPower">Aumentar</button>
    <button @click="downPower">Disminuir</button>
   
</template>

<script>
export default {
    data(){

        return {
            brand: 'Seat',
            model: 'Leon',
            color: ['Azul', 'Rojo', 'Verde'],
            price: 38000,
            power: 180,
            mensaje: {
                title: 'Hola mundo',
                text: 'Adios'
            }
        };
    },

    methods: {
        upPower(){
            this.power++;
        },

        downPower(){
            this.power--;
        }
    },

    components: {
        
        
    }
};
</script>

<style>

</style>