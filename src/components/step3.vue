<template>
  <div class="container">
    <div class="row">
      <div class="col-4">
        <div class="img-wrapper">
          <img v-if="isCatVisible"
               v-bind:style="imgStyles"
               src="http://placekitten.com/300/300"
               v-bind:class="imgFilters"
          >
          <p v-else>The cat will be back soon</p>
        </div>
      </div>
      <div class="col-4">
        <div class="controls">
          <h1>Cat</h1>
          <h2>Filters</h2>
          <div class="btn-group flex">
            <button
                type="button"
                v-bind:class="imgFilters.sepia ? 'active' : ''"
                v-on:click="imgFilters.sepia = !imgFilters.sepia"
            >
              Sepia
            </button>
            <button
                type="button"
                v-bind:class="imgFilters.border ? 'active' : ''"
                v-on:click="imgFilters.border = !imgFilters.border"
            >
              Border
            </button>
            <button
                type="button"
                v-bind:class="imgFilters.small ? 'active' : ''"
                v-on:click="imgFilters.small = !imgFilters.small"
            >
              Decrease
            </button>
          </div>
          <h2>Size</h2>
          <div class="btn-group">
            <label>
              Width: {{ imgSizes.currentWidth }}
              <input
                  type="range"
                  v-on:input="imgSizes.currentWidth = $event.target.value"
                  v-bind:value="imgSizes.currentWidth"
                  v-bind:min="imgSizes.minWidth"
                  v-bind:max="imgSizes.maxWidth"
              >
            </label>
            <label>
              Height: {{ imgSizes.currentHeight }}
              <input
                  type="range"
                  v-on:input="imgSizes.currentHeight = $event.target.value"
                  v-bind:value="imgSizes.currentHeight"
                  v-bind:min="imgSizes.minHeight"
                  v-bind:max="imgSizes.maxHeight"
              >
            </label>
          </div>
          <h2>Rotate</h2>
          <div class="btn-group">
            <label>
              Angle: {{ imgRotation.currentAngle }}
              <br>
              <input
                  type="range"
                  v-on:input="imgRotation.currentAngle = $event.target.value"
                  v-bind:min="imgRotation.minAngle"
                  v-bind:max="imgRotation.maxAngle"
              >
            </label>
          </div>

          <br>
          <button
              v-on:click="isCatVisible = !isCatVisible"
              style="margin: 10px;"
              v-if="isCatVisible == true"
          >
            Hide cat
          </button>
          <button
              v-on:click="isCatVisible = !isCatVisible"
              style="margin: 10px;"
              v-else
          >
            Show cat
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "step3.vue",
  data() {
    return {
      isCatVisible: true,
      imgFilters: {
        sepia: false,
        border: false,
        small: false,
      },
      imgSizes: {
        maxWidth: 300,
        maxHeight: 300,
        currentWidth: 300,
        currentHeight: 300,
      },
      imgRotation: {
        maxAngle: 360,
        minAngle: 0,
        currentAngle: 0,
      },
    }
  },
  computed: {
    imgStyles() {
      return {
        width: `${this.imgSizes.currentWidth}px`,
        height: `${this.imgSizes.currentHeight}px`,
        transform: `rotate(${this.imgRotation.currentAngle}deg)`,
      }
    },
  }
}
</script>

<style lang="scss" scoped>
img {
  transition: 0.2s ease;

  &.sepia {
    filter: sepia(100%);
  }

  &.border {
    border: 5px dashed #42b983;
  }

  &.small {
    width: 100px;
  }
}

button {
  margin: 10px;

  &.active {
    background-color: aqua;
  }
}
</style>
