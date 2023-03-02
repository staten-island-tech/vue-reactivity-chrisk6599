<template>
  <h1>{{ student }}</h1>
  <ul>
    <li v-for="animal in animals" :key="animal">{{ animal }}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      student: "E",
      animals: ["pig", "cow"],
    };
  },
};
</script>
