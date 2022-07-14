<template>
  <h1>Input</h1>
  <textarea v-model="inputValue"></textarea>

  <h1>Transformer</h1>
  <textarea v-model="transformerValue"></textarea>

  <pre>{{ transforResult }}</pre>

  <button @click="transform">Transform</button>
</template>

<script>
import { JsonMap } from "jsonmap-js"

const transformer = new JsonMap()

export default {
  name: 'HelloWorld',

  data() {
    return {
      transforResult: ''
    }
  },

  methods: {
    transform() {
      this.transforResult = transformer.transform(this.inputValue, this.transformerValue)

      console.log(this.transforResult)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
