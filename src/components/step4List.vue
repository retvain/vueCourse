<template>
  <div class="root">
    <div class="container-lg">
      <h1 class="mx-3 my-3 text-4xl">Writing desks</h1>
      <step4-input
                   v-on:clickFind="clickFind"
      >

      </step4-input>

      <div class="flex flex-row">
        <div
            class="mx-1 w-1/3"
            v-for="(product, index) in products"
            v-bind:key="index"
        >
          <step4-card
              v-bind:title="product.title"
              v-bind:price="product.price"
              v-bind:img-url="product.imgUrl"
              v-bind:count="product.count"
              v-on:addToBasket="addToBasket(index)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import step4Card from "./step4Card";
import Step4Input from "./step4Input";

export default {
  name: "step4",
  components: {Step4Input, step4Card},
  data() {
    return {
      toggle: '',

      products: [
        {
          title: 'Table "Sherlock"',
          price: 19999,
          imgUrl: 'https://hoff.ru/upload/iblock/3e1/3e1218b232f5d5c379accb2ff26c4bd9.jpg',
          count: 20,
        },
        {
          title: 'Table "Jim"',
          price: 17199,
          imgUrl: 'https://hoff.ru/upload/iblock/dc2/dc267a8dfd79b9b2ae1f7301262d0414.jpg',
          count: 27,
        },
        {
          title: 'Table "Slim-2"',
          price: 21999,
          imgUrl: 'https://hoff.ru/upload/iblock/704/704bd197655bd9772d6a145a57c54c9b.jpg',
          count: 18,
        },
      ]
    }
  },
  methods: {
    addToBasket(index) {
      console.log(index);
    },
    clickFind(searchText) {
      console.log(searchText);
    }
  }
}
</script>

<style scoped>

</style>