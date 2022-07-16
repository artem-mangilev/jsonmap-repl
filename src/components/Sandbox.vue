<template>
  <div class="wrapper">
    <div class="textareas">
      <div class="textarea-block">
        <h2>Input</h2>
        <textarea class="textarea" v-model="inputValue"></textarea>
      </div>

      <div class="textarea-block">
        <h2>Transformer</h2>
        <textarea class="textarea" v-model="transformerValue"></textarea>    
      </div>
    </div>

    <button @click="transform">Transform</button>
  </div>

  <pre class="result">{{ transforResult }}</pre>
</template>

<script>
import { JsonMap } from "jsonmap-js"

const transformer = new JsonMap({ space: 2 })

export default {
  name: 'Sandbox',

  data() {
    return {
      transforResult: ''
    }
  },

  methods: {
    transform() {
      this.transforResult = transformer.transform(this.inputValue, this.transformerValue)
    }
  }
}
</script>

<style scoped>
  .wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  .textareas {
    flex-basis: 100%;
    width: 1000px;
    margin: 0 auto;
    display: flex;
  }

  .textarea {
    width: 500px;
    height: 400px;
    max-width: 500px;
    max-height: 400px;
  }

  .result {
    flex-basis: 100%;
  }
</style>
