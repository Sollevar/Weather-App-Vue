<script setup>
import Input from './Input.vue';
import Button from './Button.vue';
import LocationIcon from '../icons/LocationIcon.vue';
import { onMounted, ref } from 'vue';
const emit = defineEmits({
    citySelect: null,
})
const isEdited = ref(false);
const currentCity = ref('Moscow');

function select() {
    isEdited.value = false;
    emit('citySelect', currentCity.value);
}

function edit() {
    isEdited.value = true;
}

onMounted(()=>{
    emit('citySelect', currentCity.value);
})

const vFocus = {
    mounted: (el) =>  el.focus(),
}


</script>
<template>
    <div class="city-select">
        <div v-if="isEdited" class="select">
            <Input v-model="currentCity" v-focus placeholder="Введите город" @keyup.enter="select()" />
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