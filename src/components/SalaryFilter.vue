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
        { title: "RMO-RM1,000", count: 1023, value: "rm0-rm1,000" },
        { title: "RM1,000-RM2,000", count: 1023, value: "rm1,000-rm2,000" },
        { title: "RM2,000-RM3,000", count: 1023, value: "rm2,000-rm3,000" },
        { title:"RM3,000-RM4,000", count: 1023, value:"rm3,000-rm4,000" },
        { title:"RM4,000-RM5,000", count: 1023, value: "rm4,000-rm5,000" },
        { title:"RM5,000-RM6,000", count: 1023, value: "rm5,000-rm6,000" },
        { title:"RM6,000-RM7,000", count: 1023, value: "RM6,000-RM7,000" },
        { title:"Above RM8,000", count: 1023, value: "Above RM8,000" }
      ],
      form: {},
    };
  },
  methods: {
    emitValue() {
      this.$emit("salary-filter", this.form);
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
