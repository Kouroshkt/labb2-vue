<template>
  <div>
    <div class="select">
    <h1 >Välj en övning och lägg till till ett pass</h1>
    <select v-model="selectedExercise">
      <option id="option" disabled value="">Välj en övning</option>
      <option v-for="exercise in gym" :key="exercise" :value="exercise">
        {{ exercise }}
      </option>
    </select>
    </div>

    <div class="buttons">
      <button @click="addExercise(1)">Lägg till i PASS 1</button>
      <button @click="addExercise(2)">Lägg till i PASS 2</button>
      <button @click="addExercise(3)">Lägg till i PASS 3</button>
      <button @click="addExercise(4)">Lägg till i PASS 4</button>
    </div>

    <div class="daymeny">
      <div class="day">
        <h3>PASS 1</h3>
        <ul>
          <li v-for="(exercise, index) in pass1" :key="index">
            <label class="exercise-label">{{ exercise }}</label>
            <button class="remove-btn" @click="removeExercise(1, index)">Ta bort</button>
          </li>
        </ul>
      </div>
      <div class="day">
        <h3>PASS 2</h3>
        <ul>
          <li v-for="(exercise, index) in pass2" :key="index">
            <label class="exercise-label">{{ exercise }}</label>
            <button class="remove-btn" @click="removeExercise(2, index)">Ta bort</button>
          </li>
        </ul>
      </div>
      <div class="day">
        <h3>PASS 3</h3>
        <ul>
          <li v-for="(exercise, index) in pass3" :key="index">
            <label class="exercise-label">{{ exercise }}</label>
            <button class="remove-btn" @click="removeExercise(3, index)">Ta bort</button>
          </li>
        </ul>
      </div>
      <div class="day">
        <h3>PASS 4</h3>
        <ul>
          <li v-for="(exercise, index) in pass4" :key="index">
            <label class="exercise-label">{{ exercise }}</label>
            <button class="remove-btn" @click="removeExercise(4, index)">Ta bort</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const gym = ref([
  "Knäböj 5 x 6-12",
  "Utfall 5 x 6-12",
  "Benspark 5 x 6-12",
  "Vadpress 5 x 6-12",
  "Kladdning 5 x 15-20",
  "Militärpress 5 x 6-12",
  "Lutande hantelpress 5 x 6-12",
  "Arnoldpress 5 x 6-12",
  "Sidolyft 5 x 6-12",
  "Kabelflyes 5 x 6-12",
  "Triceps pushdown i kabel 5 x 6-12",
  "Latsdrag / chins 5 x 6-12",
  "Hantelrodd 5 x 6-12",
  "Russian twist 5 x 6-12",
  "Lårcurl 5 x 6-12",
  "Marklyft 5 x 6-12",
  "Skivstångscurl 5 x 6-12"
]);

// Vald övning
const selectedExercise = ref("");

// Passen där övningar ska läggas till
const pass1 = ref<string[]>([]);
const pass2 = ref<string[]>([]);
const pass3 = ref<string[]>([]);
const pass4 = ref<string[]>([]);

const addExercise = (passNumber: number) => {
  const pass = getPass(passNumber);
  if (selectedExercise.value && !pass.includes(selectedExercise.value)) {
    pass.push(selectedExercise.value);
    selectedExercise.value = "";  // Rensa valt värde efter tillägg
  } else if (pass.includes(selectedExercise.value)) {
    alert("Denna övning är redan tillagd i detta pass.");
  } else {
    alert("Välj en övning först!");
  }
};

const getPass = (passNumber: number) => {
  if (passNumber === 1) return pass1.value;
  if (passNumber === 2) return pass2.value;
  if (passNumber === 3) return pass3.value;
  if (passNumber === 4) return pass4.value;
  return [];
};

const removeExercise = (passNumber: number, index: number) => {
  const pass = getPass(passNumber);
  pass.splice(index, 1);
};
</script>

<style scoped>
.select{
  text-align: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.select select{
  background-color: antiquewhite;
  border-radius: 5px;
  height: 30px;
}
.buttons{
  display: grid;
  grid-template-columns: repeat(4,1fr);
}
.daymeny {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  background-color: #f8f9fa;
  padding: 20px;
  border-radius: 10px;
}

.day {
  background-color: #fff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-family: 'Trebuchet MS';
  text-align: center;
  padding: 20px;
  border-radius: 10px;
  transition: transform 0.2s ease;
}

.day:hover {
  transform: scale(1.05);
}

h3 {
  font-size: 1.5em;
  color: #333;
  margin-bottom: 10px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  font-size: 1.2em;
  margin: 5px 0;
  color: #555;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.exercise-label {
  background-color: #ffc107;
  color: #000;
  padding: 5px 10px;
  border-radius: 5px; 
}

button.remove-btn {
  background-color: #b93945;
  color: #fff;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button.remove-btn:hover {
  background-color: #910917;
}

button {
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}
@media (min-width: 800px) and (max-width: 1100px) {
.buttons{
  grid-template-columns: repeat(2,1fr);
}
.daymeny {
  grid-template-columns: repeat(1, 1fr);
}
.select select{
  height: 35px;
  width: 250px;
}
}
@media (max-width: 799px) {
h1{
    font-size: 20px;
  }
.buttons{
  grid-template-columns: repeat(1,1fr);
}
button{
  font-size: 15px;
}
.daymeny {
  grid-template-columns: repeat(1, 1fr);
}
.select select{
  height: 35px;
  width: 250px;
}
}

</style>
