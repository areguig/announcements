<template>
  <div id="app">
    <img alt="logo" src="./assets/logo.png" />
    <Quotes :content="content" />
  </div>
</template>

<script>
import Quotes from "./components/Quotes.vue";

export default {
  name: "app",
  data: function() {
    return {
      content: []
    };
  },
  components: {
    Quotes
  },
  methods: {
    fetchData: function() {
      fetch("./data/it_quotes.json").then(response => {
        response.json().then(a => (this.content = a));
      });
    }
  },
  created: function() {
    this.fetchData();
    console.log("data fetched");
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
