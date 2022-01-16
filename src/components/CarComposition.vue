<template>
    <h2>Car - Composition API</h2>
    <p>Marca: {{  brand }}</p>
    <p>Modelo: {{  model }}</p>
    <p>Color:
        <ul>
            <li v-for="(color, index) in colors" :key="index">
                <span>{{index}} : {{color}}</span>
            </li>
        </ul>
    </p>
    <p>Precio: {{  price }} €</p>
   
    <p>Potencias urbanas menor a 300 cv</p>
    <ul>
        <template v-for="(power, index) in powers" :key="index">
            <li v-if="power < 280">
                Urbana: {{power}}
            </li>
            <li v-else-if="power === 280">
                Híbrido: {{power}}
            </li>
            <li v-else>
                Carrera: {{power}}
            </li>
        </template>
    </ul>

    <p>Power: {{ power }}</p>

    <button @click="upPower(100)">Aumentar</button>
    <button @click="downPower(100)">Disminuir</button>

    <p>Mensaje: {{  mensaje.title }} - {{ mensaje.text }}</p>
</template>

<script>
import { ref } from 'vue';

export default {
    setup(){
        const brand = 'Audi';
        const model = 'A4';
        const colors = ['Azul', 'Morado', 'Marron'];
        const price = 45000;
        let power = ref(40);
        const powers = [60, 80, 120, 160, 200, 280, 300, 390, 540, 500];
        const mensaje = {
            title: 'Estoy bien',
            text: 'Welcome'
        };

        const upPower = (val) => {
            console.log('aumenta');
            power.value+= val;
        };

        const downPower = (val) => {
            console.log('disminuye');
            power.value-= val;
        };

        return {
            brand, 
            model, 
            colors, 
            price, 
            power, 
            powers, 
            mensaje,
            upPower,
            downPower
        }
    },

    components: {
        
    }
};
</script>

<style>

</style>