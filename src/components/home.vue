<template>
  <div class="hello">
    <div class="hero-image">
      <div class="hero">
        <img src="../assets/Hero.png" />
        <div class="text">
          <h1>bēon</h1>
          <br>
          <h3>Dēsign Agēncy</h3>
          <h4>Meet Our Designers</h4>
          <div class="whiteIcons">
            <div class="number"><img id="email" src="../assets/white-email.png" />
              <p>bēon@design.nz</p>
            </div>
            <div class="number"><img id="phone" src="../assets/white-phone.png" />
              <p>03 321 12345</p>
            </div>
          </div>
        </div>
        <div class="Scroll-arrow">
          <img class="arrow" src="../assets/arrow.png" />
        </div>
      </div>
    </div>
    <!-- card containers -->
    <div class="container">
      <projectCard userID="mdoolaard499f"></projectCard>
    </div>
    <br>
    <div class="container">
      <projectCard userID="northlandscapes"></projectCard>
    </div>
    <br>
    <div class="container">
      <projectCard userID="FraserMacedo"></projectCard>
    </div>
    <br>
    <div class="container">
      <projectCard userID="JARLEHc8f1"></projectCard>
    </div>

  </div>

</template>

<script>
import projectCard from '@/components/projectCard'
import Vue from 'vue'
window.Vue = Vue

export default {
  name: 'home',
  components: { projectCard: projectCard },
  data () {
    return {}
  },

  methods: {},
  mounted () {}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  height: 100%;
}

h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
h1 {
  position: absolute;
  top: 30%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  letter-spacing: 15px;
  font-size: 40px;
}
h3 {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  letter-spacing: 1px;
  font-weight: 100;
  font-size: 12px;
}
h4 {
  position: absolute;
  top: 60%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  letter-spacing: 5px;
  font-size: 30px;
}
.number {
  background-color: transparent;
  color: white;
}
#phone,
#email {
  height: 40px;
  width: 30px;
}
.whiteIcons {
  text-align: center;
  margin: -100px;
}
p {
  color: white;
  margin: 12px;
}
.phone,
.email {
  height: 40px;
  width: 30px;
  margin-top: -50px;
}
.hero-icon {
  margin-bottom: 50px;
}
.Scroll-arrow {
  padding-bottom: 50px;
  padding: 50px 20px 50px;
  text-align: center;
}
.arrow {
  height: 50px;
  width: 50px;
}
.container {
  background-color: #f7f7f7;
  padding: 30px;
}
.card {
  background-color: white;
}
.image {
  width: auto;
  height: 100%;
  vertical-align: middle;
}
</style>
