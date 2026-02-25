<script setup>
import LeftPanel from './components/LeftPanel.vue';
import RightPanel from './components/RightPanel.vue';
import { onMounted, provide, ref, watch } from 'vue';

const API_ENDPOINT = 'https://api.weatherapi.com/v1'; // базовый url запроса к API

const data = ref();
const error = ref(); // будет хранится информация ошибок при запросе к API
const activeIndex = ref(0);
const currentCity = ref('Москва');
provide('currentCity', currentCity);

watch(currentCity, () =>{
  getCity(currentCity.value);
});

onMounted(() =>{
  getCity(currentCity.value);
})

async function getCity(city) {
  const params = new URLSearchParams({
    q: city,
    lang: 'ru',
    key: '',
    days: 3,
  });
  const res = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`);
  if (res.status !== 200) {
    error.value = await res.json();
    data.value = null;
    return;
  }
  error.value = null;
  data.value = await res.json();
}

</script>

<template>
  <main class="main">
    <LeftPanel
    v-if="data"
    :data="data.forecast.forecastday[activeIndex]"
    :currentCity="currentCity"
    />
    <RightPanel 
    :data="data"
    :error="error"
    :active-index="activeIndex"
    @select-index="(index) => activeIndex = index"
    />
  </main>
</template>


<style scoped>
.main{
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
