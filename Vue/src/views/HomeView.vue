<script>
import Button from "../components/Button.vue";
// import Card from "../components/Card.vue";
import ArrayList from "../components/ArrayList.vue";

export default {
  name: "home",
  components: {
    Button,
    // Card,
    ArrayList,
  },
  methods: {
    add: function (item) {
      this.total.push(item);
      console.log(this.total);
    },
    // hi: function () {
    //   console.log("hi");
    // },
    // bye: function () {
    //   console.log("bye");
    // },
  },
};
</script>

<template>
  <div class="home">
    <ArrayList></ArrayList>
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
