<template>
  <div id="flexDiv">
    <Button @click="display()">Click</Button>
    <div id="bigDiv" style="display: none">
      <div class="output" v-for="(cartItems, index) in shoppingCart">
        {{ checkItem(cartItems, index) }}
        <p>{{ cartItems.name }}</p>
        <p>${{ cartItems.price }}</p>
        <p>Quantity: {{ cartItems.count }}</p>
        <p>Total: ${{ cartItems.total.toFixed(2) }}</p>
        <img v-bind:src="cartItems.image" class="cool" />
      </div>
      <div>Total: ${{ finalTotal.toFixed(2) }}</div>
    </div>

    <div v-for="(item, index) in items" class="test">
      <p>{{ item.name }}</p>
      <img v-bind:src="item.image" />
      <p>${{ item.price }}</p>
      <Button @click="decrease(item)">-</Button>
      <input
        type="text"
        :class="classCreation(index)"
        v-bind:value="item.count"
        readonly
      />
      <Button @click="increase(item)">+</Button>
      <Button @click="addToCart(item, index)">Add to Cart</Button>
    </div>
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
    addToCart: function (item, index) {
      let testing = `.quantityItems${index}`;
      item.count = item.count + Number(document.querySelector(testing).value);

      document.querySelector(testing).value = 0;
    },

    checkItem: function (cartItems, index) {
      if (cartItems.count == 0) {
        this.shoppingCart.splice(index, 1);
      }
    },

    increase: function (item) {
      item.count++;
      item.total = item.total + item.price;
      this.finalTotal = this.finalTotal + item.price;

      let matched = this.shoppingCart.filter(
        (element) => element.name === item.name
      );
      if (matched.length == 0) {
        this.shoppingCart.push(item);
      }
    },

    decrease: function (item) {
      let matched = this.shoppingCart.filter(
        (element) => element.name === item.name
      );
      if (matched.length != 0 && item.count > 0) {
        item.count -= 1;
        item.total = item.total - item.price;
        this.finalTotal = this.finalTotal - item.price;
      }
    },

    display: function () {
      if (this.visibility == true) {
        document.getElementById("bigDiv").style.display = "none";
        this.visibility = false;
      } else {
        document.getElementById("bigDiv").style.display = "block";
        this.visibility = true;
      }
    },

    classCreation(index) {
      return `quantityItems${index}`;
    },
  },
  data() {
    return {
      visibility: false,
      items: [
        {
          name: "Rock1",
          image:
            "https://outforia.com/wp-content/uploads/2021/07/Types-of-rocks-quartzite-0721.jpg",
          price: 0.05,
          count: 0,
          total: 0,
        },
        {
          name: "Rock2",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 13,
          count: 0,
          total: 0,
        },
      ],
      shoppingCart: [],
      finalTotal: 0,
    };
  },
};
</script>

<style scoped>
#flexDiv {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
.output {
  font-size: 10px;
}

.cool {
  width: 100px;
}
.test {
  margin-top: 2rem;
}
</style>
