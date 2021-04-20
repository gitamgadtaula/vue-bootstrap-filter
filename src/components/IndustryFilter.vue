<template>
  <div v-if="show">
    <div class="card">
      <ul>
        <li v-for="(item, index) in options" :key="index">
          <input type="checkbox" v-model="form[item.value]" />
          {{ item.title }} ({{ item.count }})
        </li>
      </ul>
      <button @click="clear">Clear all</button>
      <button @click="emitValue">Apply</button>
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
        { title: "sales and marketing", count: 33, value: "sales_marketing" },
        { title: "item 2", count: 313, value: "item_1" },
        { title: "item 3", count: 213, value: "item_2" },
        { title: "item 4", count: 113, value: "item_3" },
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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
