<template>
  <section>
    <Button @click="display()">Click</Button>
    <div id="bigDiv" style="display: none">
      <div id="output" v-for="(cartItems, index) in shoppingCart">
        <p>{{ cartItems.name }}</p>
        <p>${{ cartItems.price }}</p>
        <p>Quantity: {{ cartItems.count }}</p>
        <p>Total: ${{ cartItems.total }}</p>
        <img v-bind:src="cartItems.image" id="imagePopup" />
      </div>
      <div>Total: ${{ finalTotal }}</div>
    </div>
  </section>

  <div id="cardDiv">
    <div v-for="(item, index) in items">
      <p>{{ item.name }}</p>
      <img v-bind:src="item.image" />
      <p>${{ item.price }}</p>
      <Button id="buttonIncrement" @click="decrease(item, index)">-</Button>
      <input
        id="numericalDisplay"
        type="text"
        :class="classCreation(index)"
        v-bind:value="item.count"
        readonly
      />
      <Button id="buttonIncrement" @click="increase(item)">+</Button>
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

    decrease: function (item, index) {
      let matched = this.shoppingCart.filter(
        (element) => element.name === item.name
      );
      if (matched.length != 0 && item.count > 0) {
        item.count -= 1;
        item.total = item.total - item.price;
        this.finalTotal = this.finalTotal - item.price;
      }

      if (item.count == 0) {
        this.shoppingCart.splice(index, 1);
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
            "https://sdrocksupply2.flywheelsites.com/wp-content/uploads/2020/11/Crushed-Granite-0.375-inch-1000-x-1000.jpg",
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
#buttonIncrement,
#numericalDisplay {
  width: 3rem;
  font-size: 1rem;
}

#cardDiv {
  width: 50%;
}

img {
  width: 10rem;
}

#output {
  font-size: 10px;
}

#imagePopup {
  width: 2rem;
}
</style>
