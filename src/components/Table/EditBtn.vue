<template>
  <button class="editBtn editBtn_edit" 
    @click="$emit('editing', editCheck())"
    v-if="props.editing === false"></button>

  <button class="editBtn editBtn_save" 
    @click="$emit('editing', editCheck())"
    v-else></button>
</template>

<script setup>
defineEmits(['editing'])
const props = defineProps(['editing'])

//Проверка статуса редактируемости
function editCheck() {
    if (props.editing === false) {
        return true 
    } else {
        return false
    }
}
</script>

<style scoped lang="scss">
    .editBtn {
        height: 30px;
        width: 30px;
        background-size: cover;
        background-color: transparent;
        border: none;

        &_edit {
            background-image: url('../../assets/icons/icons8-edit-30.svg');
        }

        &_save {
            background-image: url('../../assets/icons/icons8-check.svg');
        }
    }
</style>