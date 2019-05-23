<template>
  <div class="hello">
    <h1>Area : HelloWorld.vue</h1>
    <p>{{ msg }}</p>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.hello {
  border: solid 10px black;
  margin: 10px;

}
</style>
