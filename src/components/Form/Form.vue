<template>
  <form action="" class="addingForm" @submit.prevent>
    <div class="addingForm__element addingForm__element_name">
        <label for="name" class="addingForm__inputName">Имя</label>
        <input type="text" id="name" class="addingForm__input" v-model="newWorker.name">
    </div>
    <div class="addingForm__element addingForm__element_surname">
        <label for="surname" class="addingForm__inputName">Фамилия</label>
        <input type="text" id="surname" class="addingForm__input" v-model="newWorker.surname">
    </div>
    <div class="addingForm__element addingForm__element_exp">
        <label for="exp" class="addingForm__inputName">Стаж</label>
        <input type="number" id="exp" class="addingForm__input" v-model="newWorker.exp">
    </div>
    <div class="addingForm__element addingForm__element_age">
        <label for="age" class="addingForm__inputName">Возраст</label>
        <input type="number" id="age" class="addingForm__input" v-model="newWorker.age">
    </div>
    <div class="addingForm__element addingForm__element_adress">
        <label for="adress" class="addingForm__inputName">Адрес</label>
        <textarea id="adress" class="addingForm__input" v-model="newWorker.adress"></textarea>
    </div>
    <button class="addingForm_btn" 
        :disabled='disabled' 
        @click="$emit('add', createObj(newWorker) ,clear(newWorker))">
        Добавить
    </button>
    <div class="addingForm__alert" >Заполните все поля формы!</div>
  </form>
</template>

<script setup>
import { reactive, computed } from "vue";
defineEmits(['add'])

//Инициализация  реактивного массива
let newWorker = reactive({
    name: '',
    surname: '',
    exp: '',
    age: '',
    adress: '',
});

//Валидация кнопки
let disabled = computed(() => {
    return ((newWorker.name !== '') 
            && (newWorker.surname !== '')
            && (newWorker.age !== '')
            && (newWorker.exp !== 0)
            &&(newWorker.adress !== ''))
                ? false : true
})

//Функция для клонирования обьекта, чтобы не пушился 
// один и тот же реактивный обьект
function createObj (obj) {
            return Object.assign({}, obj)
            clear(newWorker)
    }

//Функция-очистка
function clear (obj) {
    for (let key in obj) {
        obj[key] = ''
    }
}

</script>

<style scoped lang="scss">
.addingForm {
    position: relative;
    width: 100%;
    gap: 20px;
    color: black;
    display: grid;
    grid-template-columns: repeat (3, 2fr);
    grid-template-rows: repeat (2, 1fr);
    grid-template-areas: 
        'name surname adress'
        'age exp adress'
    ;
    margin: 50px 0;
    padding: 20px;
    border: solid black 1px;
    border-radius: 20px;
    background-color: grey;
    
    .addingForm__element {
        display: flex;
        justify-content: space-between;
        font-family: 'Roboto-Medium';
    }

    .addingForm__input {
        background-color: transparent;
        border: 1px solid black;
        border-radius: 10px;
        padding: 5px;
        text-align: center;
        word-break: break-word;
        font-family: 'Roboto-Light';
    }
    .addingForm__element_name {
        grid-area: name;
    }

    .addingForm__element_surname {
        grid-area: surname;
    }

    .addingForm__element_age {
        grid-area: age;
    }

    .addingForm__element_exp {
        grid-area: exp;
    }

    .addingForm__element_adress {
        grid-area: adress;
        overflow-wrap: break-word;
    }

    .addingForm_btn {
        color: black;
        background-color: green;
        max-width: 120px;
        padding: 10px;
        border: 2px solid black;
        border-radius: 50px;

        &:disabled {
            background-color: red;
        }
    }

    .addingForm__alert {
        position: absolute;
        bottom: 15px;
        right: 15px;
        font-family: 'Roboto-Medium';
        color: rgb(105, 44, 44);
    }
}
</style>