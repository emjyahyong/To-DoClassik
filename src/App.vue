<template>
    <div id="app">
      <h1>Bienvenue sur To-DoClassik</h1>
      <p v-show="show">Aucune tâche</p>
      <button @click="add">Ajouter</button>
      {{ cpunt }}
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'

  </script>
  
  <style>
  #app {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 50px;
  }
  </style>
  