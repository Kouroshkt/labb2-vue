<template>
    <div class="image-gallery">
      <button @click="previousImage">←</button> <!-- Vänster-knapp -->
      
      <img :src="currentImage" alt="Gym image" class="gymImage" /> <!-- Aktuell bild -->
      
      <button @click="nextImage">→</button> <!-- Höger-knapp -->
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const num = ref(1); // Starta från 1
  const currentImage = ref(`/1.jpg`);
  
  function nextImage() {
    if (num.value < 5) {
      num.value++;
      currentImage.value = `/${num.value}.jpg`;
    }
  }
  
  function previousImage() {
    if (num.value > 1) {
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
    width: 200px;
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
  