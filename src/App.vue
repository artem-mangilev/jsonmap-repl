<template>
  <h1>Jsonmap</h1>

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
