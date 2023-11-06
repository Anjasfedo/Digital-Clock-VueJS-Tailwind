<script setup>
import {ref, onMounted, onBeforeUnmount} from 'vue'

const date = ref(new Date(Date.now()))

const hour = ref(date.value.getHours())
const minute = ref(date.value.getMinutes())
const second = ref(date.value.getSeconds())

const updateDate = () => {
  date.value = new Date(Date.now());
  hour.value = date.value.getHours()
  minute.value = date.value.getMinutes()
  second.value = date.value.getSeconds()
}
const intervalId = ref(null);
onMounted(() => {
      intervalId.value = setInterval(updateDate, 1000);
    });

    onBeforeUnmount(() => {
      clearInterval(intervalId.value);
    });
</script>

<template>
<div class="bg-black h-full flex justify-center items-center flex-col">
  <div class="text-white mb-24">
    <h1 class="text-8xl font-extrabold">Digital Clock</h1>
  </div>
  <h1 class="text-4xl bg-emerald-800 font-bold rounded-xl p-10">{{ hour }} : {{ minute }} : {{ second }}</h1>
</div>
</template>

<style scoped>

</style>
