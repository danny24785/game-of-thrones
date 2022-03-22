<template>
  <div id="app">
    <HelloWorld msg="Winter is coming"/>

    <div class="filters">
      Gender: 
      <select v-model="selectedGender">
        <option v-for="gender in genders" v-bind:key="gender.id">{{ gender.name }}</option>
      </select>

      IsAlive: 
      <select v-model="selectedIsAlive">
        <option v-for="alive in isAlive" v-bind:key="alive.id">{{ alive.name }}</option>
      </select>
    </div>

    <ol>
      <li v-for="character in characters" v-bind:key="character.id" class="character-details">
        <ul>
          <li v-if="character.name">Name: {{ character.name }}</li>
          <li v-if="character.gender">Gender: {{ character.gender }}</li>
          <li v-if="!character.died">Is alive: Yes</li>
          <li v-else>Is alive: No ( died {{ character.died }} )</li>
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
      // Feed
      characters: undefined,
      
      // Filters
      genders: [
        {id: 1, name: 'Male'},
        {id: 2, name: 'Female'},
        {id: 3, name: 'Not specified'}
      ],
      isAlive: [
        {id: 1, name: 'Yes'},
        {id: 2, name: 'No'}
      ]
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
