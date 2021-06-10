<template>
  <div class="container">
    <div class="row">
      <div class="col-4">
        <div class="img-wrapper">
          <img v-show="isCatVisible" src="http://placekitten.com/300/300">
          <!--      <p v-else>The cat will be back soon</p>-->
        </div>
      </div>
      <div class="col-4">
        <div class="controls">
          <h1>Cat</h1>
          <button v-on:click="isCatVisible = !isCatVisible">
            Show / hide
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "step3.vue",
  data () {
    return {
      isCatVisible: true

    }
  },
}
</script>

<style lang="scss" scoped>
img {
  &.sepia {
    filter: sepia(100%);
  }
  &.border {
    border: 5px;
  }
  &.small {
    width: 100px;
  }
}
</style>
