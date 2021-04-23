<template>
<div class="all_cards">
  <div v-if="show">
    <div class="card">
      <!-- <div class="search_company">
        <input type="text" placeholder="Search company">
        <img  src="../assets/search.svg">
        </div> -->
      <ul>  
        <li v-for="(item, index) in options" :key="index">
          <label class="container">
          <input type="checkbox" v-model="form[item.value]" />
          <span class="checkmark"></span>
          <span class="title">{{ item.title }}</span> <span class="count">({{ item.count }})</span>
          </label>
        </li>
      </ul>
      <div class="card_buttons">
      <button class="clear" @click="clear">Clear all</button>
      <button class="apply" @click="emitValue">Apply</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      options: [
        { title: "Fresh graduates", count: 1023, value: "fresh_graduates" },
        { title: "1 - 3 Years", count: 1023, value: "1-3_years" },
        { title: "3 - 5 Years", count: 1023, value: "3-5_years" },
        { title: "5 - 10 Years", count: 1023, value: "5-10_years" },
        { title: "Above 10 Years", count: 1023, value: "above10years" },
            
      ],
      form: {},
    };
  },
  methods: {
    emitValue() {
      this.$emit("experience-filter", this.form);
    },
    clear() {
      //clear the form
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul li:first-child{
  padding-top:0;
}

</style>
