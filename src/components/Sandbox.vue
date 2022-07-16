<template>
  <div ref="errorToast" class="toast align-items-center">
    <div class="d-flex">
      <div class="toast-body">
        {{ errorMessage }}
      </div>
      <button type="button" class="btn-close me-2 m-auto" data-bs-dismiss="toast" aria-label="Close"></button>
    </div>
  </div>

  <div class="wrapper">
    <div class="textareas">
      <div class="textarea-block">
        <h2>Input</h2>
        <textarea class="textarea form-control" v-model="inputValue"></textarea>
      </div>

      <div class="textarea-block">
        <h2>Transformer</h2>
        <textarea class="textarea form-control" v-model="transformerValue"></textarea>    
      </div>
    </div>

    <button class="btn btn-primary" @click="transform">Transform</button>
  </div>

  <pre class="result">{{ transforResult }}</pre>
</template>

<script>
import { Toast } from "bootstrap"
import { JsonMap } from "jsonmap-js"

const transformer = new JsonMap({ space: 2 })

export default {
  name: 'Sandbox',

  data() {
    return {
      transforResult: '',
      errorMessage: ''
    }
  },

  methods: {
    transform() {
      try {
        this.transforResult = transformer.transform(this.inputValue, this.transformerValue) 
      } catch (error) {
        this.errorMessage = error.message
        this.errorToast.show()
      }
    }
  },

  mounted() {
    this.errorToast = new Toast(this.$refs.errorToast)
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
    justify-content: space-between;
  }

  .textarea {
    width: 450px;
    height: 400px;
    max-width: 450px;
    max-height: 400px;
  }

  .result {
    flex-basis: 100%;
  }
</style>
