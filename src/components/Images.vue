<template>
  <div class="image-gallery">
    <button @click="previousImage">←</button> <!-- Vänster-knapp -->
    <img :src="leftImage" alt="Gym image" class="gymImage" /> 
    <img :src="currentImage" alt="Gym image" class="gymImage" /> 
    <button @click="nextImage">→</button> <!-- Höger-knapp -->
  </div>
</template>

<script setup>
import { ref } from 'vue';

const num = ref(2); // Starta från bild 2
const leftImage = ref(`/1.jpg`);
const currentImage = ref(`/2.jpg`);

function nextImage() {
  if (num.value < 5) {
    leftImage.value = `/${num.value}.jpg`;
    num.value++;
    currentImage.value = `/${num.value}.jpg`;
  }
}

function previousImage() {
  if (num.value > 2) {
    leftImage.value = `/${num.value - 2}.jpg`;
    num.value--;
    currentImage.value = `/${num.value}.jpg`;
  }
}
</script>

<style>
.image-gallery {
  display: flex;
  align-items: center;
  justify-content: center;
}

.gymImage {
  width: 300px;
  height: 300px;
  object-fit: cover;
  margin: 0 10px;
}

button {
  background-color: #f0f0f0;
  border: none;
  padding: 10px;
  cursor: pointer;
  font-size: 18px;
}

button:hover {
  background-color: #ddd;
}
</style>
