<template>
  <div class="flex flex-row">
    <!--      <input type="text" class="ml-1 mb-3 " v-bind:value="searchText" v-on:input="searchText = $event.target.value">-->
    <input type="text" class="ml-1 mb-3 "
           v-model="searchText"

    >
    <button type="button" class="btn btn-success ml-1 mb-3" v-on:click="clickFind(searchText)">find</button>

  </div>
</template>

<script>
export default {

  methods: {
    clickFind(searchText) {
      this.$emit('clickFind', searchText)
    }
  },
  data() {
    return {
      searchText: '',
    }
  }
}
</script>

<style scoped>

</style>