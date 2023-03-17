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
    add: function () {
      this.total.push(this.item);
      console.log(this);
      console.log(this.total);
    },
    // hi: function () {
    //   console.log("hi");
    // },
    // bye: function () {
    //   console.log("bye");
    // },
  },
  data() {
    return {
      items: [
        {
          name: "Rock1",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 12,
        },
        {
          name: "Rock2",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 13,
        },
      ],
      total: [],
    };
  },
};
</script>

<template>
  <div class="home">
    <!-- <ArrayList> -->
    <div v-for="item in items" class="test">
      <p>{{ item.name }}</p>
      <img v-bind:src="item.image" />
      <p>${{ item.price }}</p>
      <Button @button-click="add">Test</Button>
    </div>
    <!-- </ArrayList> -->
    <!-- <Button @button-click="bye">Button One</Button>
    <Button @button-click="hi">Button Two</Button>
    <Card
      title="Hello"
      description="Hi"
      image="https://media.sproutsocial.com/uploads/2017/02/10x-featured-social-media-image-size.png"
    ></Card> -->
  </div>
</template>

<style>
.test {
  background-color: red;
  margin-top: 2rem;
}
</style>
