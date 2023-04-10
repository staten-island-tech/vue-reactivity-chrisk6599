<template>
  <ItemDisplay
    v-for="(item, index) in items"
    :className="classCreation(index)"
    :name="item.name"
    :image="item.image"
    :price="item.price"
  ></ItemDisplay>
</template>

<script>
import ItemDisplay from "./ItemDisplay.vue";
export default {
  name: "Card",
  components: {
    ItemDisplay,
  },
  methods: {
    classCreation(index) {
      return `numberDisplay${index}`;
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
        },
        {
          name: "Crushed Granite",
          image:
            "https://sdrocksupply2.flywheelsites.com/wp-content/uploads/2020/11/Crushed-Granite-0.375-inch-1000-x-1000.jpg",
          price: 87.5,
        },
        {
          name: "Crushed Limestone",
          image:
            "https://www.braenstone.com/wp-content/uploads/2021/06/open-graded-1-1-2-crushed-limestone-1264x1264.jpg",
          price: 25,
        },
        {
          name: "Lava Rock",
          image:
            "https://eadn-wc01-7017865.nxedge.io/cdn/media/catalog/product/cache/56479904931fb76a498cfc2b7870f50d/g/e/ge-lrs-a-08-20.jpg",
          price: 167.5,
        },
        {
          name: "Pea Gravel",
          image:
            "https://texasgardenmaterials.com/wp-content/uploads/2018/08/pea-gravel-rock-sugar-land-tx-77498.jpg",
          price: 37.5,
        },
      ],
      finalTotal: 0,
    };
  },
};
</script>

<style scoped>
* {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;

  margin: 0rem 0rem 2rem 2rem;
}
</style>
