<template>
  <div class="flex flex-col items-center select-none">
    <h1 class="text-4xl mt-12">Hola Euge</h1>
    <h2 :class="[siClickeado ? 'text-2xl text-warm-pink' : 'text-lg']">{{ msg }}</h2>
    <div>
      <img src="./assets/loop-cute-love-cub.gif" alt="Cute love cub" draggable="false" />
    </div>
    <div>
      <button
        id="btnSi"
        class="border-2 rounded-xl bg-rose-pink border-warm-pink px-6 relative -left-2 z-50 hover:"
        @click="cambiarMsg"
      >
        Sí
      </button>
      <button
        class="border-2 rounded-xl px-6 relative bg-white cursor-default"
        :style="{
          left: offset.left,
          top: offset.top,
        }"
        @mouseover="moveBtn"
      >
        No
      </button>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from "vue";
const offset = reactive({ top: "0px", left: "8px" });
const msg = ref("¿Salimos a comer?");
const siClickeado = ref(false);

function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min) + min);
}

function moveBtn(e) {
  offset.left =
    getRandomInt(
      -(window.innerWidth - e.clientX) / 2,
      (window.innerWidth - e.clientX) / 2
    ).toString() + "px";
  offset.top =
    getRandomInt(
      -(window.innerHeight - e.clientY) / 2,
      (window.innerHeight - e.clientY) / 2
    ).toString() + "px";
  console.log(offset);
}

function cambiarMsg() {
  msg.value = "Nos vemos el viernes 22 a la noche ;)";
  siClickeado.value = true;
}
</script>

<style scoped>
#btnSi:hover {
  transition: 100ms;
  transform: scale(1.1);
}
</style>
