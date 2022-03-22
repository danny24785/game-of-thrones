<template>
  <div id="app">
    <HelloWorld msg="Winter is coming"/>
    <pre>
    <!-- {{ characters }} -->

    <!--

      Feed is paginated, use ?use=<page-number> to navigate between pages

      -->
    </pre>
    <ol>
      <li v-for="character in characters" v-bind:key="character.id" class="character-details">
        <ul>
          <li v-if="character.name">Name: {{ character.name }}</li>
          <li v-if="character.gender">Gender: {{ character.gender }}</li>
          <li v-if="character.died">Is alive: {{ character.died }}</li>
        </ul>
      </li>  
    </ol>
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
      .get('https://anapioficeandfire.com/api/characters?page=1&pageSize=40')
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

.character-details {
  margin: 0 0 1rem 0;
}
</style>
