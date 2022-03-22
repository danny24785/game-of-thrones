<template>
  <div id="app">
    <AppTitle msg="Winter is coming"/>

    <!-- <pre>{{ characters }}</pre> -->

    <div class="filters">
      Gender: 
      <select class="inputSelect">
        <option v-for="gender in genders" v-bind:key="gender.id">{{ gender.name }}</option>
      </select>

      IsAlive: 
      <select class="inputSelect">
        <option v-for="alive in isAlive" v-bind:key="alive.id">{{ alive.name }}</option>
      </select>

      <button class="resetFilter button filterButton">
        Reset filters
      </button>
    </div>

    <Feed 
      :characters="characters"
    />
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue'
import Feed from './components/Feed.vue'
import axios from "axios";

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
      .get('https://anapioficeandfire.com/api/characters?page=1&pageSize=10')
      .then(response => (this.characters = response.data))
      .catch(error => console.log(error))
  },
  components: {
    AppTitle,
    Feed
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

.filterButton {
  margin: 0 0 0 1rem;
}

.button:hover,
.inputSelect:hover {
  cursor: pointer;
}
</style>
