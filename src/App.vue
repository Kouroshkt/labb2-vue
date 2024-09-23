<script setup>
import Day from './components/Day.vue';
import Header from './components/Header.vue';
import Images from './components/Images.vue';

function theme() {
  // Byter bakgrundsfärg och textfärg på body-elementet
  const body = document.body;
  if (body.style.backgroundColor === 'rgb(209, 228, 228)') {
    body.style.backgroundColor = 'rgb(112, 206, 206)'; // Mörkt tema
    body.style.color = rgb(123, 10, 204); // Textfärg
  } else {
    body.style.backgroundColor = 'rgb(209, 228, 228)'; // Ljust tema
    body.style.color = 'brown'; // Textfärg
  }
}
</script>

<template>
  <button id="buttonTheme" @click="theme">Change Theme</button>
  <Header/>
  <Images/>
  <Day/>
</template>
<style>
@media (max-width: 799px){
 #buttonTheme{
  font-size: 12px;
 }
}

</style>