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
    <br />
    <Button id="addToCartButton" @click="addToCart(className, name)"
      >Add to Cart</Button
    >
  </div>
</template>

<script>
import Button from "./Button.vue";
import { shoppingCart } from "./ShoppingCart.vue";

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
      let matched = shoppingCart.filter((element) => element.name === name);
      if (matched.length == 0) {
        shoppingCart.push({
          name: this.name,
          image: this.image,
          price: this.price,
          count: Number(document.querySelector(`.${className}`).value),
        });
      } else {
        shoppingCart.forEach(function (element, index) {
          if (element.name == name) {
            shoppingCart[index].count += Number(
              document.querySelector(`.${className}`).value
            );
          }
        });
      }
      document.querySelector(`.${className}`).value = 0;
    },
  },
};
</script>

<style scoped>
#individualCard {
  border: solid black;
  padding: 2rem;
  width: 30%;
}

#buttonIncrement,
#numericalDisplay {
  width: 2rem;
  height: 2rem;
  text-align: center;
  vertical-align: middle;
  margin-top: 0.5rem;
}

img,
h3,
#addToCartButton {
  margin-top: 0.5rem;
}

img {
  width: 20%;
}
</style>
