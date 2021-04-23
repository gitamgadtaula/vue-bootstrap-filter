<template>
<div class="all_cards">
  <div v-if="show">
    <div class="card">
      <!-- <div class="search_company">
        <input type="text" placeholder="Search company">
        <img  src="../assets/search.svg">
        </div> -->
      <ul>  
          <h5>Transport accessibility</h5>
        <li v-for="(item, index) in transport_accessibility" :key="index">
          <label class="container">
          <input type="checkbox" v-model="form[item.value]" />
          <span class="checkmark"></span>
          <span class="title">{{ item.title }}</span>
          </label>
        </li>
      </ul>
      <ul>  
          <h5>Travelling</h5>
        <li v-for="(item, index) in travelling_options" :key="index">
          <label class="container">
          <input type="checkbox" v-model="form[item.value]" />
          <span class="checkmark"></span>
          <span class="title">{{ item.title }}</span>
          </label>
        </li>
      </ul>
      <ul> 
          <h5>Special group - Health condition</h5> 
        <li v-for="(item, index) in special_group" :key="index">
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
      transport_accessibility: [
          {title:"Distance from public access"},
          {title:"Shutter bus available"},
            
      ],
      travelling_options: [
          {title: "High > 50%"},
          {title: "Moderate < 20-50%"},
          {title: "Low < 20%"},
      ],
      special_group:[
          {title:"OKU", count: 1023},
          {title:"Non-OKU", count: 1023},
      ],
      form: {},
    };
  },
  methods: {
    emitValue() {
      this.$emit("others-filter", this.form);
    },
    clear() {
      //clear the form
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul:first-child, ul:nth-child(2){
    border-bottom: 1px solid #ECECEC;
}
ul{
  margin:0;
}
.container{
  margin:0px 16px 8px 16px;
}
ul h5{
  font-size:12px;
  color:#858585;
  margin-bottom:6px;
  margin-left:16px;
  margin-right:16px;
  }
.card{
  padding-top: 4px;
}
</style>
