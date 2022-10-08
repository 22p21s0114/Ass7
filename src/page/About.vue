<template>
  <div>
    <Navbar />
    <section class="about">
      <h1 class="heading">about <span>me</span></h1>

      <div class="row">
        <div class="info-container">
          <h1>personal info</h1>

          <div class="box-container">
            <div class="box">
              <h3><span>name : </span> {{ name }}</h3>
              <h3><span>age : </span> {{ age }}</h3>
              <h3><span>email : </span> {{ email }}</h3>
              <h3><span>address : </span> {{ address }}</h3>
            </div>

            <div class="box">
              <h3><span>freelance : </span> unavailable</h3>
              <h3><span>skill : </span>Financail Engineer</h3>
              <h3><span>experience : </span> 1 years</h3>
              <h3><span>language : </span> Thai / Portugues / Spainsh</h3>
            </div>
          </div>

          <a href="/profilewithcss/files/resume.pdf" class="btn">
            download CV <i class="fas fa-download"></i>
          </a>
        </div>

        <div class="count-container">
          <div class="box">
            <h3>1</h3>
            <p>years of experience</p>
          </div>

          <div class="box">
            <h3>1</h3>
            <p>happy clients</p>
          </div>

          <div class="box">
            <h3>2</h3>
            <p>project completed</p>
          </div>

          <div class="box">
            <h3>6</h3>
            <p>Certificates</p>
          </div>
        </div>
      </div>
    </section>

    <!-- about section ends -->

    <!-- skills section starts  -->

    <section class="skills">
      <h1 class="heading"><span>my</span> skills</h1>

      <div class="box-container">
        <div class="box" v-for="e in skill" :key="e.image">
          <img :src="e.image" />
          <h3>{{ e.name }}</h3>
        </div>
      </div>
    </section>

    <!-- skills section ends -->

    <!-- education section starts  -->

    <section class="education">
      <h1 class="heading"><span>my</span> experience</h1>

      <div class="box-container">
        <div class="box" v-for="e in experaince" :key="e.years">
          <i class="fas fa-briefcase"></i>
          <span>{{ e.years }}</span>
          <h3>{{ e.company }}</h3>
          <p>{{ e.jobs }}</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Navbar from "../components/navbar.vue";
import axios from "axios";
export default {
  components: { Navbar },
  methods: {
    async fetchexperience() {
      try {
        let res = await axios.get(
          "https://633fc566e44b83bc73c0f545.mockapi.io/profile/v1/experiences"
        );
        this.experaince = res.data;
      } catch (error) {}
    },
    async fetchskill() {
      try {
        let res = await axios.get(
          "https://633fc566e44b83bc73c0f545.mockapi.io/profile/v1/skills "
        );
        this.skill = res.data;
      } catch (error) {}
    },
  },
  data() {
    return {
      name: "Krittin Hiangrat",
      age: "24",
      email: "kaokong.spk@hotmail.com",
      address: " Mahasarakham, Thailand 44000",
      experaince: [],
      skill: [],
    };
  },
  beforeMount() {
    this.fetchexperience();
    this.fetchskill();
  },
};
</script>

<style>
</style>