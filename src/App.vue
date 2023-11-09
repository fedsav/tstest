<script setup>
import Table from './components/Table/Table.vue';
import Form from './components/Form/Form.vue';
import { reactive } from 'vue';



let workers = reactive ([])
</script>

<template>
  <Form @add="(w) => workers.push(w)"/>
  <Table :workers="workers"/>
</template>

<style scoped>

</style>
