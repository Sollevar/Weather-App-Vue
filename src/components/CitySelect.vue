<script setup>
import Input from './Input.vue';
import Button from './Button.vue';
import LocationIcon from '../icons/LocationIcon.vue';
import { inject, ref } from 'vue';

const isEdited = ref(false);
const currentCity = inject('currentCity');
const inputValue = ref(currentCity.value)

function select() {
    isEdited.value = false;
    currentCity.value = inputValue.value;
}

function edit() {
    isEdited.value = true;
}

const vFocus = {
    mounted: (el) =>  el.focus(),
}

</script>
<template>
    <div class="city-select">
        <div v-if="isEdited" class="select">
            <Input v-model="inputValue" v-focus placeholder="Введите город" @keyup.enter="select()" />
            <Button @click="select()">
                Сохранить
            </Button>
        </div>
        <Button v-else @click='edit()'>
            <LocationIcon />
            Изменить город
        </Button>
    </div>
</template>
<style scoped>
.select {
    display: flex;
    height: 61px;
    gap: 12px;
}
</style>