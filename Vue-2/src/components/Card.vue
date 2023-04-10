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
import { shoppingCart } from "./ShoppingCart.vue";
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
          name: "Hydrogen",
          image: "https://energyeducation.ca/wiki/images/8/88/HYDROGEN.png",
          price: 1.39,
        },
        {
          name: "Helium",
          image:
            "https://energyeducation.ca/wiki/images/thumb/f/f0/HELIUM.png/200px-HELIUM.png",
          price: 24,
        },
        {
          name: "Lithium",
          image:
            "https://media.istockphoto.com/id/654559838/vector/lithium-periodic-table-element-gray-icon-on-white-background-vector.jpg?s=612x612&w=0&k=20&c=Z4esXSRFufmrVOYc6fYlU1EuqTZgRuEyHhj_xGzUZtc=",
          price: 81.49,
        },
        {
          name: "Beryllium",
          image: "https://energyeducation.ca/wiki/images/a/a2/Be.png",
          price: 857,
        },
        {
          name: "Boron",
          image:
            "https://previews.123rf.com/images/tony4urban/tony4urban1801/tony4urban180100040/93637645-boron-chemical-element-periodic-table-science-symbol.jpg",
          price: 3.69,
        },
        {
          name: "Carbon",
          image:
            "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCjW-YJbcFs0Gp0-lGrMRKpzQ6j2Qhhj3RwA&usqp=CAU",
          price: 0.13,
        },
        {
          name: "Nitrogen",
          image:
            "https://previews.123rf.com/images/tony4urban/tony4urban1801/tony4urban180100109/93551403-nitrogen-chemical-element-periodic-table-science-symbol.jpg",
          price: 0.14,
        },
        {
          name: "Oxygen",
          image:
            "https://media.istockphoto.com/id/1195265997/vector/oxygen-periodic-table-of-the-elements-vector-illustration-eps-10.jpg?s=612x612&w=0&k=20&c=PSXxj37WQQVxZLLoGQg6q11Wi1GSbsd1go-QU9dcpvw=",
          price: 0.15,
        },
        {
          name: "Fluorine",
          image:
            "https://previews.123rf.com/images/tony4urban/tony4urban1801/tony4urban180100124/93521580-fluorine-chemical-element-periodic-table-science-symbol.jpg",
          price: 1.84,
        },
        {
          name: "Neon",
          image:
            "https://previews.123rf.com/images/tony4urban/tony4urban1801/tony4urban180100058/93545718-neon-chemical-element-periodic-table-science-symbol.jpg",
          price: 240,
        },
        {
          name: "Sodium",
          image:
            "https://thumbs.dreamstime.com/b/sodium-periodic-table-elements-vector-illustration-eps-161995316.jpg",
          price: 2.57,
        },
        {
          name: "Magnesium",
          image:
            "https://thumbs.dreamstime.com/b/magnesium-periodic-table-elements-vector-illustration-eps-161995152.jpg",
          price: 2.32,
        },
      ],
      finalTotal: 0,
    };
  },
};
</script>

<style scoped>
* {
  margin: 0rem 0rem 2rem 2rem;
  text-align: center;
}
</style>
