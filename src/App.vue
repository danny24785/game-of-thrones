<template>
  <div id="app">
    <AppTitle msg="Winter is coming"/>

    <div class="filters">
      Gender: 
      <select class="inputSelect" @change="selectedGender()">
        <option selected disabled>Select gender</option>
        <option v-for="gender in genders" v-bind:key="gender.id">{{ gender.name }}</option>
      </select>

      IsAlive: 
      <select class="inputSelect">
        <option selected disabled>Select isAlive</option>
        <option v-for="alive in isAlive" v-bind:key="alive.id">{{ alive.name }}</option>
      </select>

      <button class="resetFilter button filterButton">
        Reset filters
      </button>
    </div>

    <Feed 
      :characters="characters"
    />

    <button @click="nextPage()">Next ({{ currentPage }})</button>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue'
import Feed from './components/Feed.vue'

export default {
  name: 'App',
  data(){
    return {
      // Feed
      characters: [],
      apiUrl: 'https://anapioficeandfire.com/api/characters',
      currentPagePrefix: '?page=',
      currentPage: 1,
      pageSizePrefix: '&pageSize=',
      pageSize: 10,
      
      // Filters
      genders: [
        {id: 1, name: 'Male'},
        {id: 2, name: 'Female'}
      ],
      isAlive: [
        {id: 1, name: 'Yes'},
        {id: 2, name: 'No'}
      ]
    }
  },
  components: {
    AppTitle,
    Feed
  },
  created() {
    let apiLink = this.apiUrl + this.currentPagePrefix + this.currentPage + this.pageSizePrefix + this.pageSize;
    fetch(apiLink)
      .then(res => res.json())
      .then(res => (this.characters = res))
      .catch(error => console.log(error));
  },
  watch: {
    selectedGender() {
      this.characters = this.characters + '&gender=Female'
    }
  },
  methods: {
    nexPage() {
      this.currentPage = this.currentPage + 1;
    }
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
