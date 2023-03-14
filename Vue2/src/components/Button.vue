<template>
  <button><slot></slot></button>
</template>

<script>
export default {
  name: "Button",
};
</script>

<style>
button {
  width: 200px;
  font-size: 20px;
  background-color: red;
}
</style>
