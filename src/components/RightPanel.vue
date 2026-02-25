<script setup>
import { computed } from 'vue';
import Error from './Error.vue';
import Statistic from './Statistic.vue';
import DayCard from './DayCard.vue';
import CitySelect from './CitySelect.vue';

const { data, error, activeIndex } = defineProps({
    data: Object,
    error: Object,
    activeIndex: Number,
});
const emit = defineEmits({
    selectIndex: null,
});

const errorMap = new Map([[1006, 'Указанный город не найден']]);
const errorDisplay = computed(() => {
    return errorMap.get(error?.error?.code);
})

const activeData = computed(()=>{
    return data.forecast.forecastday[activeIndex].day;
})

const statData = computed(() => {
    return [
        {
            label: 'Вероятность осадков',
            value: `${activeData.value.daily_chance_of_rain}` + ' %',
        },
        {
            label: 'Влажность',
            value: `${activeData.value.avghumidity}` + ' %',
        },
        {
            label: 'Ветер',
            value: `${activeData.value.maxwind_kph}` + ' км/ч',
        },
    ]
});

</script>

<template>
    <div class="right-panel">
        <Error v-if="error" :error="errorDisplay" />
        <div v-if="data">
            <div class="statistic-list">
                <Statistic v-for="data in statData" v-bind="data" :key="data.label" />
            </div>
            <div class="card-days">
                <DayCard v-for="(item, index) in data.forecast.forecastday" :temp="item.day.avgtemp_c"
                    :date="new Date(item.date)" :weather-code="item.day.condition.code" :key="item.date"
                    :is-active="activeIndex == index" @click="emit('selectIndex', index)" />
            </div>
        </div>
        <CitySelect/>
    </div>
</template>

<style scoped>
.right-panel {
    min-width: 615px;
    position: relative;
    flex-direction: column;
    display: flex;
    padding: 60px 50px 60px 70px;
    border-radius: 25px;
    background-color: var(--app-color);
}

.statistic-list {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.card-days {
    margin: 35px 0;
    display: flex;
    justify-content: center;
    gap: 5px
}
</style>