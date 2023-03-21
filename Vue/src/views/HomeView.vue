<script>
// import Card from "../components/Card.vue";
import Button from "../components/Button.vue";
import ArrayList from "../components/ArrayList.vue";

export default {
  name: "home",
  components: {
    // Card,
    Button,
    ArrayList,
  },
  // hi: function () {
  //   console.log("hi");
  // },
  // bye: function () {
  //   console.log("bye");
  // },
  methods: {
    display: function () {
      document
        .querySelector(".outputButton")
        .addEventListener("click", function () {
          document.querySelector(".output").innerHTML = ArrayList.data;
        });
    },
  },
};
</script>

<template>
  <div class="home">
    <Button @click="display()" class="outputButton">Shopping Cart</Button>
    <div class="output"></div>
    <ArrayList> </ArrayList>
    <!-- <Button @button-click="bye">Button One</Button>
    <Button @button-click="hi">Button Two</Button>
    <Card
      title="Hello"
      description="Hi"
      image="https://media.sproutsocial.com/uploads/2017/02/10x-featured-social-media-image-size.png"
    ></Card> -->
  </div>
</template>

<style></style>
