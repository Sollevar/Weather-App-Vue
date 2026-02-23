<script setup>
import LocationIcon from '../icons/LocationIcon.vue';
import SunnyIcon from '../icons/weather/SunnyIcon.vue';
</script>

<template>
    <div class="panel left-panel">
        <div class="panel__top">
            <span class="panel__day">
                Tuesday
            </span>
            <span class="panel__date">
                20 Jun 2022
            </span>
            <span class="panel_location">
                <LocationIcon :size="27" />
                Biarritz, FR
            </span>
        </div>
        <div class="panel__bottom">
            <SunnyIcon />
            <span class="panel__temp">
                29 °C
            </span>
            <span class="panel__temp-text">
                Sunny
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

.panel__date {
    font-weight: 500;
    font-size: 22px;
}

.panel_location {
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

.panel__temp {
    font-weight: 700;
    font-size: 50px
}

.panel__temp-text {
    font-weight: 700;
    font-size: 30px;
}
</style>