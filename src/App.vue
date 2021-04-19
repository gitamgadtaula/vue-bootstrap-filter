<template>
  <div id="app">
    <p>list items like this</p>
    <button @click="toggleIndustry">Industry</button>
    <industry-filter :show="showIndustry" />
  </div>
</template>

<script>
import IndustryFilter from "./components/IndustryFilter.vue";
export default {
  name: "App",
  components: { IndustryFilter },
  data() {
    return {
      showIndustry: false,
    };
  },
  methods: {
    toggleIndustry() {
      this.showIndustry = !this.showIndustry;
    },
  },
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
