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

    <div class="cardDiv">
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
      </div>
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
          name: "Boulder",
          image:
            "https://media.istockphoto.com/id/684455306/photo/big-rock.jpg?s=612x612&w=0&k=20&c=x4EvkRacFbGA7i2kanzOFkULh6UWzlHfl4Vb5t3XsaQ=",
          price: 350,
          count: 0,
          total: 0,
        },
        {
          name: "Crushed Granite",
          image:
            "https://media.istockphoto.com/id/684455306/photo/big-rock.jpg?s=612x612&w=0&k=20&c=x4EvkRacFbGA7i2kanzOFkULh6UWzlHfl4Vb5t3XsaQ=",
          price: 87.5,
          count: 0,
          total: 0,
        },
        {
          name: "Crushed Limestone",
          image:
            "https://www.braenstone.com/wp-content/uploads/2021/06/open-graded-1-1-2-crushed-limestone-1264x1264.jpg",
          price: 25,
          count: 0,
          total: 0,
        },
        {
          name: "Lava Rock",
          image:
            "https://eadn-wc01-7017865.nxedge.io/cdn/media/catalog/product/cache/56479904931fb76a498cfc2b7870f50d/g/e/ge-lrs-a-08-20.jpg",
          price: 167.5,
          count: 0,
          total: 0,
        },
        {
          name: "Pea Gravel",
          image:
            "https://texasgardenmaterials.com/wp-content/uploads/2018/08/pea-gravel-rock-sugar-land-tx-77498.jpg",
          price: 37.5,
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
img {
  width: 10rem;
}

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
  justify-content: space-evenly;
}

.cardDiv {
  margin-top: 2rem;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
