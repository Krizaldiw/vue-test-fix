<template>
  <div class="row">
    <div
      class="card"
      style="width: 15rem;"
      v-for="item in products"
      :key="item.id"
    >
      <img :src="item.imgUrl" class="card-img-top" :alt="item.title" />
      <div class="card-body">
        <p class="card-title">{{ item.title }}</p>
        <p class="card-text">$ {{ item.price.toLocaleString() }}</p>
        <button class="btn btn-warning" @click="addItemToCart(item)">
          Add to cart
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Shop",
  mounted() {
    this.getProducts();
  },
  computed: {
    ...mapGetters(["products"]),
  },
  methods: {
    ...mapActions(["addItemToCart", "getProducts"]),
  },
};
</script>

<style scoped>
.card {
  padding: 20px;
  margin: 5px;
  border: 1;
}
</style>
