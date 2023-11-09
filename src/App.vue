<script setup>
import Table from './components/Table/Table.vue';
import Form from './components/Form/Form.vue';
import { reactive } from 'vue';



let workers = reactive ([
  {
    name: 'Alex',
    surname: 'Moscoff',
    exp: 2,
    age: 28,
    adress: 'Russi Moscow Kolotushkina 22, 42'
  },
  {
    name: 'Lexa',
    surname: 'Peterec',
    exp: 4,
    age: 23,
    adress: 'Russi Spb Kalova 56'
  }
])
</script>

<template>
  <Form @add="(w) => workers.push(w)"/>
  <Table :workers="workers"/>
</template>

<style scoped>

</style>
