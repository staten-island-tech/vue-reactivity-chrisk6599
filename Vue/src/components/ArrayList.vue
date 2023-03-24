<template>
  <div id="flexDiv">
    <Button @click="display()">Click</Button>
    <div id="bigDiv" style="display: none">
      <div class="output" v-for="cartItems in shoppingCart">
        <p>{{ cartItems.name }}</p>
        <p>${{ cartItems.price }}</p>
        <p>Quantity: {{ cartItems.count }}</p>
        <p>Total: ${{ cartItems.total }}</p>
        <img v-bind:src="cartItems.image" class="cool" />
      </div>
    </div>

    <div v-for="item in items" class="test">
      <p>{{ item.name }}</p>
      <img v-bind:src="item.image" />
      <p>${{ item.price }}</p>
      <Button @click="add(item)">Test</Button>
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
    add: function (item) {
      item.count++;
      item.total = item.total + item.price;

      let matched = this.shoppingCart.filter(
        (element) => element.name === item.name
      );
      if (matched.length == 0) {
        this.shoppingCart.push(item);
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
  },
  data() {
    return {
      visibility: false,
      items: [
        {
          name: "Rock1",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 12,
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
  background-color: red;
  margin-top: 2rem;
}
</style>
