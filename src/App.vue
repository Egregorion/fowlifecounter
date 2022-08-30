<template>
  <div>
    <Player :isFirst="true" />
    <Player :isFirst="false" />
  </div>  
</template>

<script>
import Player from './components/Player.vue'
export default {
  name: 'App',
  components: {
    Player
  },
}
</script>

<style>
   body{
    margin:0;
    font-size:2em;
    text-shadow: 2px 2px 4px black;
   }
</style>
