<script setup>
import RainIcon from '../icons/weather/RainIcon.vue';
import CloudIcon from '../icons/weather/CloudIcon.vue';
import SunnyIcon from '../icons/weather/SunnyIcon.vue';
const { temp, date, weatherCode } = defineProps({
    temp: Number,
    date: Date,
    weatherCode: Number,
    isActive: Boolean,
})
</script>
<template>
    <button class="card" :class="{'card-active':isActive}">
        <div class="card__icon">
            <RainIcon v-if="weatherCode >= 1063" :color="isActive ? 'black' : 'white'" />
            <CloudIcon v-if="weatherCode >= 1006 && weatherCode < 1063" :color="isActive ? 'black' : 'white'"  />
            <SunnyIcon v-if="weatherCode <= 1003" :color="isActive ? 'black' : 'white'" />
        </div>
        <span class="card__temp">
            {{ date.toLocaleDateString("ru-Ru", { weekday: 'short' }) }}
        </span>
        <span class="card__day">{{ temp }} °C</span>
    </button>
</template>
<style scoped>
.card {
    padding: 18px 24px;
    display: flex;
    flex-direction: column;
    gap: 15px;
    align-items: center;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-size: 20px;
    background-color: var(--card-background-color);
    color: var(--primary-color);
    box-shadow: 1px 2px 4px 0 #222831;
    transition: background-color 0.2s ease-in-out;
}



.card-active {
    background-color: var(--primary-color);
    color: var(--black-color);
}

.card:not(.card-active):hover {
    background-color: #3a434f;
}

.card__day {
    font-weight: 400;
}

.card__temp {
    font-weight: 700;
}
</style>