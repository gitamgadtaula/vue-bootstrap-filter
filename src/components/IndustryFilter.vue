<template>
<div class="all_cards">
  <div v-if="show">
    <div class="card">
      <div class="search_company">
        <input type="text" placeholder="Search company">
        <img  src="../assets/search.svg">
        </div>
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
        { title: "Sales/marketing", count: 1023, value: "sales_marketing" },
        { title: "Account Finance", count: 1023, value: "account_finance" },
        { title: "IT", count: 1023, value: "it" },
        { title:"Admin HR", count: 1023, value: "admin_hr" },
        { title:"Services", count: 1023, value: "services" },
        { title:"Engineering", count: 1023, value: "engineering" },
        { title:"Education/training", count: 1023, value: "education_training" }
      ],
      form: {},
    };
  },
  methods: {
    emitValue() {
      this.$emit("industry-filter", this.form);
    },
    clear() {
      //clear the form
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search_company{
  border:1px solid #dfdfdf;
  border-radius:4px;
  background:#fff;
  padding:8px 14px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 16px;
}
.search_company input{
  border:0;
  background:none; 
}
.search_company input::placeholder{
  color:#CBCBCB;
}
.search_company img{
  width:14.6px;
  height: 14.6px;
}

</style>
