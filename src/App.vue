<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    {{this.feedUrls.default}}
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from "axios";

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return {
      xmlContent: null,
      xmlError: false,
      errorMsg: "",
      axiosLoading: false,

      feed: "default",
      characters: false,
      feedUrl: "",
      feedUrls: {
        default: 'https://anapioficeandfire.com/api/characters/'
      }
    }
  },
  methods: {
    loadData() {
      this.xmlContent = null;
      this.xmlError = false;

      
      this.axiosLoading = true;

      axios
        .get(this.feedUrl)
        .then(response => {
          let jsonObj = this.$x2js.xml2js(response.data);
          this.characters = jsonObj;
        })
        .catch(error => {
          this.xmlError = true;
          this.errorMsg = error;
        })
        .finally(
          
          () => (this.axiosLoading = false)
        );

    }
  },

  created() {
    this.feedUrl = this.feedUrls[this.feed];
    this.loadData();
  }
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
