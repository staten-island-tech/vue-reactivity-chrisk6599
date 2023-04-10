<template>
  <img
    @click="display()"
    src="https://cdn-icons-png.flaticon.com/512/263/263142.png"
  />
  {{ convert() }}
  <div id="bigDiv" style="display: none">
    <p id="totalAmount" v-if="this.usableShoppingCart.length != 0">
      Total: ${{ totalCalculation().toFixed(2) }}
    </p>
    <div id="individualCard" v-for="(item, index) in usableShoppingCart">
      <p>{{ item.name }}</p>
      <img :src="item.image" />
      <p>Quantity: {{ item.count }}</p>
      <p>${{ (item.count * item.price).toFixed(2) }}</p>
      <Button @click="removeItem(index)">Remove</Button>
    </div>
  </div>
</template>

<script>
import { reactive } from "vue";
import Button from "./Button.vue";

export const shoppingCart = reactive([]);
export default {
  name: "ShoppingCart",
  components: {
    Button,
  },
  methods: {
    removeItem(index) {
      this.usableShoppingCart.splice(index, 1);
    },
    display() {
      if (this.visibility == true) {
        document.getElementById("bigDiv").style.display = "none";
        this.visibility = false;
      } else {
        document.getElementById("bigDiv").style.display = "block";
        this.visibility = true;
      }
    },
    convert() {
      this.usableShoppingCart = shoppingCart;
    },
    totalCalculation() {
      let totalAmount = 0;
      this.usableShoppingCart.forEach(function (element) {
        totalAmount = totalAmount + element.count * element.price;
      });
      return totalAmount;
    },
  },
  data() {
    return {
      usableShoppingCart: [],
      visibility: false,
    };
  },
};
</script>

<style scoped>
img {
  margin-top: 2rem;
  height: 3rem;
}

#bigDiv {
  margin: auto;
  width: 70%;
}

#individualCard {
  border: black solid;
  margin-top: 2rem;
  padding: 1rem;
}

#totalAmount {
  font-size: 2rem;
  position: sticky;
  top: 0;
  z-index: 1;
  background-color: white;
}

button {
  width: 80%;
}
</style>
