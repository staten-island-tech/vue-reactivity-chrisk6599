<script>
import Card from "../components/Card.vue";
import Button from "../components/Button.vue";
import ArrayList from "../components/ArrayList.vue";

export default {
  name: "home",
  components: {
    Card,
    Button,
    ArrayList,
  },
  // hi: function () {
  //   console.log("hi");
  // },
  // bye: function () {
  //   console.log("bye");
  // },
  methods: {},
};
</script>

<template>
  <div class="home">
    <!-- <Card
      title="ArrayList"
      description="Hi"
      image="https://media.sproutsocial.com/uploads/2017/02/10x-featured-social-media-image-size.png"
    ></Card> -->
    <ArrayList></ArrayList>
  </div>
</template>

<style></style>
