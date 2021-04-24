<template>
  <div id="app">
    <!-- <p>list items like this</p> -->
    <div class="filters">
      <div class="filters_title">
        <div class="filter-item">
          <button @click="toggleIndustry">
            Industry <img class="chevron-up" :src="arrow(showIndustry)" />
          </button>
          <industry-filter
            :show="showIndustry"
            @industry-filter="getIndustryFilter"
          />
        </div>
        <div class="filter-item">
          <button @click="toggleSalary">
            Salary<img class="chevron-up" :src="arrow(showSalary)" />
          </button>
          <salary-filter :show="showSalary" @salary-filter="getSalaryFilter" />
        </div>
        <div class="filter-item">
          <button @click="toggleExperience">
            Experience<img class="chevron-up" :src="arrow(showExperience)" />
          </button>
          <experience-filter
            :show="showExperience"
            @experience-filter="getExperienceFilter"
          />
        </div>
        <div class="filter-item">
          <button @click="toggleCompany">
            Company<img class="chevron-up" :src="arrow(showCompany)" />
          </button>
          <company-filter
            :show="showCompany"
            @company-filter="getCompanyFilter"
          />
        </div>
        <div class="filter-item">
          <button @click="toggleOthers">
            Others<img class="chevron-up" :src="arrow(showOthers)" />
          </button>
          <others-filter :show="showOthers" @others-filter="getOthersFilter" />
        </div>
      </div>
      <!-- <div class="action_buttons">
      <button class="clear">Clear all</button>
      <button class="apply" >Apply(128)</button>
      </div> -->
    </div>
  </div>
</template>

<script>
import IndustryFilter from "./components/IndustryFilter.vue";
import SalaryFilter from "./components/SalaryFilter.vue";
import ExperienceFilter from "./components/ExperienceFilter.vue";
import CompanyFilter from "./components/CompanyFilter.vue";
import OthersFilter from "./components/OthersFilter.vue";
export default {
  name: "App",
  components: {
    IndustryFilter,
    SalaryFilter,
    ExperienceFilter,
    CompanyFilter,
    OthersFilter,
  },
  data() {
    return {
      showIndustry: false,
      showSalary: false,
      showExperience: false,
      showCompany: false,
      showOthers: false,
    };
  },
  methods: {
    arrow(value) {
      if (value) {
        return require("./assets/up-chevron.svg");
      }
      return require("./assets/down-arrow.png");
    },
    toggleIndustry() {
      this.showIndustry = !this.showIndustry;
    },
    toggleSalary() {
      this.showSalary = !this.showSalary;
    },
    toggleExperience() {
      this.showExperience = !this.showExperience;
    },
    toggleCompany() {
      this.showCompany = !this.showCompany;
    },
    toggleOthers() {
      this.showOthers = !this.showOthers;
    },
    getIndustryFilter(e) {
      console.log(e);
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap");
@import url("./assets/css/style.css");
</style>
