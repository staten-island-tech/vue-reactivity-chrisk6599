<template>
  <Button @click="display()">Click</Button>
  <div id="bigDiv">
    <div class="output" v-for="cartItems in shoppingCart">
      <p>{{ cartItems.count }}</p>
      <p>{{ cartItems.name }}</p>
      <img v-bind:src="cartItems.image" class="cool" />
      <p>{{ cartItems.price }}</p>
    </div>
  </div>

  <div v-for="item in items" class="test">
    <p>{{ item.name }}</p>
    <img v-bind:src="item.image" />
    <p>${{ item.price }}</p>
    <Button @click="add(item)">Test</Button>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "ArrayList",
  components: {
    Button,
  },
  methods: {
    add: function (item) {
      item.count++;
      let toBeAdded = true;
      this.shoppingCart.forEach(function (element) {
        if (element.name === item.name) {
          toBeAdded = false;
        }
      });
      if (toBeAdded) {
        this.shoppingCart.push(item);
      }
    },
    display: function () {},
  },
  data() {
    return {
      visibility: true,
      items: [
        {
          name: "Rock1",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 12,
          count: 0,
        },
        {
          name: "Rock2",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 13,
          count: 0,
        },
      ],
      shoppingCart: [],
    };
  },
};
</script>

<style scoped>
.output {
  font-size: 10px;
}

.cool {
  width: 100px;
}
.test {
  background-color: red;
  margin-top: 2rem;
}
</style>
