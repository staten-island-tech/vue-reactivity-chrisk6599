<template>
  <button @click=""><slot></slot></button>
</template>

<script>
export default {
  name: "Button",
};
</script>

<style scoped>
button {
  width: 200px;
  font-size: 20px;
}
</style>
