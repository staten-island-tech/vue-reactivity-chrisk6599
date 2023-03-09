<template>
  <div class="home">
    <select v-model="selected">
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
    <span>{{ selected }}</span>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      selected: "",
    };
  },
  methods: {},
};
</script>

<style scoped>
h1 {
  color: red;
}
</style>
