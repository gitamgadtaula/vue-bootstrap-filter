<template>
  <div class="">
    <div v-if="show" style="width: unset !important">
      <div class="card">
        <ul>
          <h5>Company review</h5>
          <li v-for="(item, index) in review_options" :key="index">
            <label class="container">
              <input type="checkbox" v-model="form[item.value]" />
              <span class="checkmark"></span>
              <span class="title">{{ item.title }}</span
              ><span class="count">({{ item.count }})</span>
            </label>
          </li>
        </ul>
        <ul>
          <h5>Company size</h5>
          <li v-for="(item, index) in size_options" :key="index">
            <label class="container">
              <input type="checkbox" v-model="form[item.value]" />
              <span class="checkmark"></span>
              <span class="title">{{ item.title }}</span
              ><span class="count">({{ item.count }})</span>
            </label>
          </li>
        </ul>
        <ul>
          <h5>Shift</h5>
          <li v-for="(item, index) in shift_options" :key="index">
            <label class="container">
              <input type="checkbox" v-model="form[item.value]" />
              <span class="checkmark"></span>
              <span class="title">{{ item.title }}</span>
              <span class="count">({{ item.count }})</span>
            </label>
          </li>
        </ul>
        <ul>
          <h5>Job Type</h5>
          <li v-for="(item, index) in job_types" :key="index">
            <label class="container">
              <input type="checkbox" v-model="form[item.value]" />
              <span class="checkmark"></span>
              <span class="title">{{ item.title }}</span>
              <span class="count">({{ item.count }})</span>
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
      review_options: [
        { title: "5 Star", count: 1023 },
        { title: "4 Star", count: 1023 },
        { title: "3 Star", count: 1023 },
        { title: "2 Star", count: 1023 },
        { title: "1 Star", count: 1023 },
      ],
      size_options: [
        { title: "Below 100", count: 1023 },
        { title: "100 - 200 employee", count: 1023 },
        { title: "200 - 300", count: 1023 },
        { title: "Above 500", count: 1023 },
      ],
      shift_options: [
        { title: "Shift", count: 1023 },
        { title: "Non-Shift", count: 1023 },
      ],
      job_types: [
        { title: "Part-time", count: 1023 },
        { title: "Full-time", count: 1023 },
        { title: "Internship", count: 1023 },
        { title: "Home based", count: 1023 },
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
ul:first-child,
ul:nth-child(2) {
  border-bottom: 1px solid #ececec;
}
ul {
  margin: 0;
  display: flex;
  flex-wrap: wrap;
}
li {
  width: 50%;
}
.container {
  margin: 0px 16px 8px 16px;
}

.card {
  /* width: 28%; */
  padding-top: 4px;
}
@media only screen and (max-width: 1298px) {
  .card {
    /* width: 50%; */
  }
}
@media only screen and (max-width: 768px) {
  .card {
    width: 100%;
  }
}
</style>
