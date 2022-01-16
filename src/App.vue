<template>
  <h1>Vue JS</h1>
 <!--  <CarOption/>
  <hr>
  <CarConmpositon/> -->
  <Car  :power = "power" 
        :upPower = "upPower"
        @downPower = "downPower"
        :kanbans = "kanbans"
        :mix = "mix" />
  
</template>

<script>
import CarConmpositon from './components/CarComposition';
import CarOption from './components/CarOption';
import Car from './components/Car';

import { ref } from 'vue';

export default {
  
  components: {
    CarConmpositon, 
    CarOption, 
    Car
  },
  setup(){
    let power = ref(30);

    let kanbans = ref([
      {
        title: 'Kanban 1',
        tasks: [
          {title: 'task1'},
          {title: 'task2'},
          {title: 'task3'},
        ]
      },
      {
        title: 'Kanban 2',
        tasks: [
          {title: 'task4'},
          {title: 'task5'},
          {title: 'task6'},
        ]
      },
      {
        title: 'Kanban 3',
        tasks: [
          {title: 'task7'},
          {title: 'task8'},
          {title: 'task9'},
        ]
      }
    ]);

    const upPower = () => {
      power.value++;
    } 

    const downPower = () => {
      power.value--;
    } 

    const mix = () =>{
        //kanbans.value[1].tasks[1].title = 'change';
        const elem = kanbans.value[1].tasks[1];

        console.log('elem', elem);

        kanbans.value[1].tasks.splice(1,1);

        kanbans.value[2].tasks.push(elem);

        //kanbans.kanbans.value[1].tasks[1].
        //console.log('kanbans', kanbans.value);
    }

    return {
      power, 
      kanbans,
      upPower, 
      downPower,
      mix
    }
  }
}
</script>

<style>

</style>