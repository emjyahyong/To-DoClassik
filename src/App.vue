<template>
  <div id="app">
    <h1>Bienvenue sur To-DoClassik</h1>
    <form action="" @submit.revent="add">
      <label for="tache">Ajouter une tâche</label>
      <input type="text" id="tache" v-model="textTache" />
      <button>Ajouter</button>
    </form>
    <p v-if="!nbTaches >= 1">Aucune tâche</p>
    <input type="checkbox" v-model="hideTaches" />
    <label v-show="hideTaches">
      <ul>
        <li
          v-for="tache in taches"
          :style="{ textDecoration: tache.completed ? 'line-through' : 'none' }"
          :key="tache.description"
        >
          <input type="checkbox" v-model="tache.completed" @submit.revent="sortTaches" />{{
            tache
          }}
        </li>
      </ul>
    </label>
  </div>
</template>

<script setup>
import { ref } from "vue";
const nbTaches = ref(0);
const textTache = ref("");
const tache = ref({
  description: "",
  completed: false,
  date: new Date(),
});
const hideTaches = ref(false);
const taches = ref([]);

const add = (event) => {
  event.preventDefault();
  nbTaches.value++;
  tache.value.description = textTache.value;
  taches.value.push(tache.value);
  taches.value.sort((a, b) => {
    return (!a.completed) - b.completed;
  });
  tache.value = {
    description: "",
    completed: false,
    date: new Date(),
  };
  textTache.value = "";
};
const sortTaches = () => {
  taches.value.sort((a, b) => {
    return (!a.completed) - b.completed;
  });
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}
</style>
