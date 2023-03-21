<template>
  <div v-for="item in items" class="test">
    <p>{{ item.name }}</p>
    <img v-bind:src="item.image" />
    <p>${{ item.price }}</p>
    <Button @click="add(item)">Test</Button>
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
      this.total.push(item);
      console.log(this);
      console.log(this.total);
    },
  },
  data() {
    return {
      items: [
        {
          name: "Rock1",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 12,
        },
        {
          name: "Rock2",
          image:
            "https://media.istockphoto.com/id/1159941628/photo/light-yellow-brown-stone-on-a-white-background.jpg?s=612x612&w=0&k=20&c=Bz9NI4dMHiJuAZK2F8zLWLS-przi4N27eQXRcq-0YF0=",
          price: 13,
        },
      ],
      total: [],
    };
  },
};
</script>

<style scoped>
.test {
  background-color: red;
  margin-top: 2rem;
}
</style>
