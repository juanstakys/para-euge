<template>
  <div class="flex flex-col items-center select-none z-1">
    <h1 class="text-4xl mt-12">Hola Euge &lt;3</h1>
    <h2 :class="[siClickeado ? 'text-2xl text-warm-pink' : 'text-lg']">{{ msg }}</h2>
    <div>
      <img
        src="./assets/loop-cute-love-cub.gif"
        alt="Cute love cub"
        draggable="false"
        class="z-2"
      />
    </div>
    <div>
      <button
        id="btnSi"
        class="border-2 rounded-xl bg-rose-pink border-warm-pink px-6 relative -left-2 z-50"
        @click="handleClick"
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
}

function handleClick() {
  msg.value = `
  Jaja, sabía que ibas a decir que sí :D.
  Nos vemos el viernes 22 a la noche ;)
  `;
  siClickeado.value = true;

  const corazonNuevo = document.createElement("span");
  // Add random size and offset
  const sizes = [
    "text-sm",
    "text-md",
    "text-lg",
    "text-xl",
    "text-2xl",
    "text-3xl",
    "text-4xl",
    "text-5xl",
    "text-6xl",
    "text-7xl",
    "text-8xl",
  ];
  const emojis = [
    "❤️",
    "💗",
    "💖",
    "💓",
    "💛",
    "🫀",
    "💝",
    "💘",
    "💞",
    "💕",
    "🥰",
    "🩷",
    "😍",
    "😘",
  ];

  const randomSize = sizes[Math.floor(Math.random() * sizes.length)];
  const randomEmoji = emojis[Math.floor(Math.random() * emojis.length)];

  corazonNuevo.appendChild(document.createTextNode(randomEmoji));
  corazonNuevo.classList.add(randomSize);

  // posicion

  corazonNuevo.style.position = "absolute";
  corazonNuevo.style.top = `${getRandomInt(0, 100)}%`;
  corazonNuevo.style.left = `${getRandomInt(0, 100)}%`;

  // Insertar en el documento
  document.body.appendChild(corazonNuevo);
}
</script>

<style scoped>
#btnSi:hover {
  transition: 100ms;
  transform: scale(1.1);
}
</style>
