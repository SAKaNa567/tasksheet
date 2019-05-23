<template>
  <div id="app">
    <!-- <HelloWorld msg="test"/> -->
    <Timer />
    <div id="app_list">
      <Form />
      <Done />
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Form from './components/Form.vue'
import Timer from './components/Timer.vue'
import Done from './components/Done.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld,
    Timer,
    Form,
    Done,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* margin-top: 60px; */
  /* border: solid 10px red; */
  height: auto;
  }
p{
  text-align: center;
}
#app_list {
  display: flex;
  justify-content: center;
}

</style>
