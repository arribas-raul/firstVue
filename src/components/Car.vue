<template>
    <h2>Car - Composition API</h2>
    <p>Marca: {{  brand }}</p>
    <p>Modelo: {{  model }}</p>
    <p>Potencia:  {{ power }}</p>

    <button @click="testPower">Aumentar</button>
    <button @click="upPower">Aumentar2</button>
    <button @click="downPower">Disminuir</button>

    <p>KANBANS</p>
    <ul>
        <template v-for="(kanban, index) in kanbans" :key="index">
            <li>
                {{kanban.title}}

                <ul>
                    <template v-for="(task, index2) in kanban.tasks" :key="index2">
                        <li>
                            {{task.title}}
                        </li>
                    </template>
                </ul>
            </li>
        </template>
    </ul>

    <button @click="mix">MIX</button>
</template>

<script>

export default {
    props: {
        power: {
            type: Number,
            default: 60
        },
        upPower: Function,
        kanbans: {
            type: Array
        },
        mix: Function
    },

    emits: [
        "downPower"
    ],

    setup(props, context){
        const brand = 'Audi';
        const model = 'A4';

        const testPower = () => {
            props.upPower();
        }

        const downPower = () => {
            context.emit("downPower");
        }

        return {
            brand, 
            model,
            testPower,
            downPower,
        }
    },

    components: {
        
    }
};
</script>

<style>

</style>