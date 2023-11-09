<template>
    <tr class="row">
        <td class="row__cell">
            <span class="row__txt" v-if="editing === false">
                {{ worker.name }}
            </span>
            <input class="row__input" type="text" v-model="worker.name" v-if="editing === true">
        </td>
        <td class="row__cell">
            <span class="row__txt" v-if="editing === false">
                {{ worker.surname }}
            </span>
            <input class="row__input" type="text" v-model="worker.surname" v-if="editing === true">
        </td>
        <td class="row__cell">
            <span class="row__txt" v-if="editing === false">
                {{ worker.exp }}
            </span>
            <input class="row__input" type="text" v-model="worker.exp" v-if="editing === true">
        </td>
        <td class="row__cell">
            <span class="row__txt" v-if="editing === false">
                {{ worker.age }}
            </span>
            <input class="row__input" type="text" v-model="worker.age" v-if="editing === true">
        </td>
        <td class="row__cell row__cell_adress">
            <span class="row__txt" v-if="editing === false">
                {{ worker.adress }}
            </span>
            <textarea class="row__input row__input_aress" rows="3" type="text" v-model="worker.adress" v-if="editing === true"></textarea>
        </td>
        <td class="row__cell row__cell_edit">
            <EditBtn @editing="(e) => editing = e" :editing="editing" />
        </td>
    </tr>
</template>

<script setup>
import EditBtn from './EditBtn.vue';
import { ref } from 'vue';
const props = defineProps(['worker'])

// Статус редактирования строки таблицы
let editing = ref(false);

</script>

<style scoped lang="scss">
    .row {
        border-bottom: 1px solid #000;
        min-height: 60px;
        padding-bottom: 5px;

        .row__cell {
            min-width: 16%;
            min-height: 20px;
            max-width: 70px;
            text-align: center;

            .row__input {
                background-color: transparent;
                text-align: center;
                max-width: 100%;
                border: none;
                font-family: 'Roboto-Light';
                font-size: 1em;
            }
        }

        .row__cell_adress {
            min-width: 120px;
            overflow-wrap: break-word;
            text-align: center;
        }
    }
</style>