<template>
<table class="maintable">
    <tr class="maintable__row">
        <td class="maintable__headcell">
            Имя
        </td>
        <td class="maintable__headcell">
            Фамилия
        </td>
        <td class="maintable__headcell">
            Стаж
        </td>
        <td class="maintable__headcell">
            Возраст
        </td>
        <td class="maintable__headcell">
            Адрес
        </td>
        <td class="maintable__headcell maintable__headcell_edit">
            
        </td>
    </tr>
    <TableRow v-for="(worker, index) in workers" 
        :key="worker" 
        :worker="workers[index]"
        class="maintable__row">
    </TableRow>
</table>
</template>

<script setup>
import TableRow from "./TableRow.vue"
const props = defineProps(['workers'])

</script>

<style scoped lang="scss">
    .maintable {
        background-color: grey;
        border: 2px solid black;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        padding: 15px 5px;
        margin: 20px;
        .maintable__row {
            display: flex;
            align-items: center;
            justify-content: space-around;
            padding-bottom: 5px;
            font-family: 'Roboto-Light';

            .maintable__headcell {
                min-width: 16%;
                text-align: center;
                font-family: 'Roboto-Medium';
            }
        }
    }
</style>