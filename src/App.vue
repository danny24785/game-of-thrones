<template>
  <div id="app">
    <HelloWorld msg="Winter is coming"/>
    <pre>
    {{ characters }}
    </pre>
    <ul v-for="character in characters" v-bind:key="character.id">
      <li>Name: {{ character.name }}</li>
      <li>Gender: {{ character.gender }}</li>
      <li>Is alive: {{ character.died }}</li>
    </ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from "axios";
// import vueAxios from "vue-axios";

export default {
  name: 'App',
  data(){
    return {
      characters: undefined
    }
  },
  mounted(){
    axios
      .get('https://anapioficeandfire.com/api/characters/')
      .then((response)=>{
        this.characters=response.data;
        console.warn(response)
      })
  },
  components: {
    HelloWorld
  },
  methods: {
    
  },

  created() {
    
  }
  
};
</script>

<style>
#app {
  text-align: left;
}
</style>
