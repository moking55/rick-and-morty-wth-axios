<script setup>
import axios from "axios";
import { ref } from "vue";

const characters = ref();

axios
  .get("https://rickandmortyapi.com/api/character")
  .then(function (response) {
    characters.value = response.data.results;
    console.log(characters.value);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>
<template>
  <div class="container">
    <center>
      <img
        style="height: 200px; margin-top: 0.5em"
        src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b1/Rick_and_Morty.svg/1200px-Rick_and_Morty.svg.png"
        alt="Logo image"
      />
      <h1 class="page-header">The rick and morty Api</h1>
    </center>
    <table>
      <thead>
        <th>Picture</th>
        <th>Name</th>
        <th>Origin</th>
        <th>Location</th>
      </thead>
      <tbody>
        <tr v-for="(character, index) in characters" :key="index">
          <td>
            <img :src="character.image" alt="Image" class="avatar-image" />
          </td>
          <td>{{ character.name }}</td>
          <td>{{ character.origin.name }}</td>
          <td>{{ character.location.name }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.page-header {
  padding-top: 0.8em;
  padding-bottom: 0.8em;
}

.avatar-image {
  height: 100px;
  width: 100px;
  object-fit: cover;
}
</style>
