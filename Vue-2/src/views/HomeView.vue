<script>
import Card from "../components/Card.vue";
import ShoppingCart from "../components/ShoppingCart.vue";

export default {
  name: "home",
  components: {
    Card,
    ShoppingCart,
  },
  methods: {},
};
</script>

<template>
  <div id="wrapperDiv">
    <div id="leftDiv"></div>
    <div id="mainDiv">
      <header>Buy Elements</header>
      <div id="flexDiv">
        <Card></Card>
      </div>
    </div>
    <div id="rightDiv">
      <ShoppingCart></ShoppingCart>
    </div>
  </div>
</template>

<style scoped>
#wrapperDiv {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

#leftDiv {
  width: 20%;
}

#mainDiv {
  width: 60%;
  text-align: center;
}

#rightDiv {
  height: 60rem;
  overflow-y: scroll;
  width: 20%;
  text-align: center;
}

#rightDiv::-webkit-scrollbar {
  display: none;
}

header {
  text-align: center;
  font-size: 4rem;
  margin: 2rem 8rem 2rem 8rem;
}

#flexDiv {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>
