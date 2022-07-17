<template>
  <h1 class="mb-2 p-2">Jsonmap</h1>

  <div class="sandbox">
    <Sandbox />
  </div>
</template>

<script>
import Sandbox from './components/Sandbox'

export default {
  name: 'App',
  components: {
    Sandbox
  }
}
</script>

<style>
  .sandbox {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }
</style>
