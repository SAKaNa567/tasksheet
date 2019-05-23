<template>
  <div class="todoitems">
    <li>
      {{ title }}
      <button v-on:click="$emit('remove')"> 🆑 </button>
    </li>

  </div>
</template>
<script>
  export default {
    name: 'TodoItem',
    props: {
      title: String
    }
  }
</script>

<style media="screen">

  li{
    text-align: center;
  }

</style>
