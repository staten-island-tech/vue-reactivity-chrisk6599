<template>
  <div id="individualCard">
    <h2>{{ name }}</h2>
    <img :src="image" />
    <h3>${{ price }}</h3>
    <Button id="buttonIncrement" @click="decrease(className)">-</Button>
    <input
      id="numericalDisplay"
      :class="className"
      type="text"
      value="0"
      readonly
    />
    <Button id="buttonIncrement" @click="increase(className)">+</Button>
    <Button @click="addToCart(className, name)">Add to Cart</Button>
  </div>
</template>

<script>
import Button from "./Button.vue";
import ShoppingCart from "./ShoppingCart.vue";

export default {
  name: "ItemDisplay",
  components: {
    Button,
  },
  props: {
    className: String,
    name: String,
    image: String,
    price: Number,
  },
  methods: {
    increase(className) {
      document.querySelector(`.${className}`).value++;
    },

    decrease(className) {
      if (document.querySelector(`.${className}`).value > 0) {
        document.querySelector(`.${className}`).value--;
      }
    },

    addToCart(className, name) {
      let matched = ShoppingCart.shoppingCart.filter(
        (element) => element.name === name
      );
      if (matched.length == 0) {
        ShoppingCart.shoppingCart.push({
          name: this.name,
          image: this.image,
          price: this.price,
          count: Number(document.querySelector(`.${className}`).value),
        });
      } else {
        ShoppingCart.shoppingCart.forEach(function (element, index) {
          console.log(element);
          if (element.name == name) {
            ShoppingCart.shoppingCart[index].count += Number(
              document.querySelector(`.${className}`).value
            );
          }
        });
      }
    },
  },
};
</script>

<style scoped>
#individualCard {
  border: solid black;
  padding: 2rem;
}

#buttonIncrement,
#numericalDisplay {
  width: 2rem;
  height: 2rem;
}

img {
  width: 20%;
}
</style>
