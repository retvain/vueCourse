<template>
  <div class="root">
    <div class="container-lg">
      <div class="grid grid-cols-2 grid-rows-2">
        <div>
          <h1 class="h3">inf about yourself</h1>
          <div
              v-for="(value, label, index ) in formFields"
              v-bind:key="index"
          >

            <label v-bind:for="label">{{ label }}: </label><br>
            <input class="form-control"
                   v-bind:id="label"
                   v-model="formFields[label]"
            ><br>

          </div>
          <button class="btn btn-dark my-3">Save</button>
        </div>

        <div class="ml-4">
          <h1 class="h3 my-3 ">Preview</h1>
          <div v-for="(value, label, index) in formFields"
          v-bind:key="index"
          >
            <p class="my-3">{{`${label}: ${value}`}}</p>
          </div>
        </div>
        <div>
          <div>
            <label for="additionalField">Additional field: </label>
          <input
              class="form-control"
              id="additionalField"
              v-model="additionalField"

          >
          </div>
          <div>
            <button
            type="button"
            class="btn btn-success mt-3"
            v-on:click="addNewField"
            > Add </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "step5",
  data() {
    return {
      formFields: {
        firstName: '',
        secondName: '',
        lastName: '',
      },
      additionalField: '',
    }
  },
  methods: {
    addNewField() {
      this.$set(this.formFields, this.additionalField, '');

    },
  }
}
</script>

<style scoped>

</style>