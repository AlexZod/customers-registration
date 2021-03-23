<template>
  <div id="app">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  height: 1920px;
  height: 800px;
  justify-content: center;
  align-items: center;
  font-size: 30px;
}

</style>
