<template>
  <h1>{{ student }}</h1>
  <ul>
    <li v-for="animal in animals" :key="animal">{{ animal }}</li>
  </ul>
  <select v-model="selected">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <h1 v-if="selected === A">Correct</h1>
  <h1 v-else-if="selected === B">Incorrect</h1>
  <h1 v-else-if="selected === C">W</h1>
  <!-- <input v-model="text" />
  <p>{{ text }}</p> -->
</template>

<script>
export default {
  data() {
    return {
      student: "E",
      animals: ["pig", "cow"],
      selected: "",
      // text: "",
    };
  },
};
</script>
