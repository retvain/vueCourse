<template>
  <div class="root">


    <div class="box-border h-50 p-1 justify-center items-center border-2">
      <img
          v-bind:src="imgUrl"
      >
      <p class="mx-3 my-3 text-lg justify-center items-center">{{ title }}</p>
      <p class="mx-3 text-sm justify-center items-center">Price: {{ price }} rub.</p>
      <p class="mx-3 my-2 text-sm text-gray-400 justify-center items-center">Available for delivery {{ count }}
        pieces</p>
      <form>
        <button type="button"
                v-on:click="addToBasket"
                class="mb-3 mt-1 mx-3 bg-red-600 text-white rounded-3 h-10 px-3 justify-center items-center">
          Add to cart.
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "step4Card",
  props: {
    title: {
      type: String,
      validator(value) {
        return value.length < 50
      }
    },
    price: {
      type: Number,
      required: true,
    },
    imgUrl: {
      type: String,
      default: 'https://www.athousakis.gr/images/usrImage/29-04-2021-10-25-608a5f517a0b8.jpg',
    },
    count: {
      type: Number,
      default: 0,
    },
},
  methods: {
    addToBasket() {
      this.$emit('addToBasket')
    }
  }

}
</script>

<style scoped>

</style>