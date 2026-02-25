<script setup>
import LocationIcon from '../icons/LocationIcon.vue';
import SunnyIcon from '../icons/weather/SunnyIcon.vue';
import RainIcon from '../icons/weather/RainIcon.vue';
import CloudIcon from '../icons/weather/CloudIcon.vue';
import { computed } from 'vue';
const { data, currentCity } = defineProps({
    data: Object,
    currentCity: String,
});

const day = computed(() => {
    return new Date(data.date).toLocaleDateString("ru-RU", {
        weekday: "long",
    });
});

const date = computed(() => {
  return new Date(data.date).toLocaleDateString("ru-RU", {
    day: "numeric",
    month: "long",
    year: "numeric",
  });
});

</script>

<template>
    <div v-if="data" class="panel left-panel">
        <div class="panel__top">
            <span class="panel__day">
               {{ day }}
            </span>
            <span class="panel__date">
                {{date}}
            </span>
            <span class="panel__location">
                <LocationIcon :size="27" />
                {{ currentCity }}
            </span>
        </div>
        <div class="panel__bottom">
            <div class="panel__temp--icon">
                <RainIcon v-if="data.day.condition.code >= 1063" :size="98" />
                <CloudIcon v-if="data.day.condition.code >= 1006 && data.day.condition.code < 1063" />
                <SunnyIcon v-if="data.day.condition.code <= 1003" />
            </div>
            <span class="panel__temp">
                {{ data.day.avgtemp_c }} °C
            </span>
            <span class="panel__temp--text">
                {{ data.day.condition.text }}
            </span>
        </div>
    </div>
</template>

<style>
.left-panel {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin: -2px -25px 0 0;
    padding: 50px 0 85px 32px;
    border-radius: 30px;
    width: 493px;
    height: 600px;
    background-image: url(../../public/left-panel-background.png);
    background-repeat: no-repeat;
    background-size: cover;
    color: var(--primary-color);
}

.panel__top {
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.panel__day {
    font-weight: 700;
    font-size: 37px;
}

.panel__day::first-letter{
    text-transform: uppercase;
}

.panel__date {
    font-weight: 500;
    font-size: 22px;
}

.panel__location {
    display: flex;
    align-items: center;
    font-weight: 600;
    font-size: 20px;
}

.panel__bottom {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.panel__temp--icon {
    padding: 0 0 25px 25px;
}

.panel__temp {
    font-weight: 700;
    font-size: 50px
}

.panel__temp--text {
    max-width: 430px;
    font-weight: 700;
    font-size: 30px;
}
</style>