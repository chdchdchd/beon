<template>
  <div id="project">
    <!-- {{ project }} -->

    <!-- <div id="app">
  <p>
    <router-link to="/user/foo">/user/foo</router-link>
    <router-link to="/user/bar">/user/bar</router-link>
  </p>
</div> -->

      <!-- <div class="columns titleAndArrow" id="app">
        <div class="column is-2 arrow-left">
          <router-link to=$route.params.id>
            <font-awesome-icon class="svg arrow" icon="angle-left"/>
          </router-link>
        </div>
        <div class="column is-8 title">
          <h2 id="title">{{ title }}</h2>
        </div>
        <div class="column arrow-right">
          <router-link to="/user/bar">
            <font-awesome-icon class="svg arrow" icon="angle-right"/>
          </router-link>
        </div>
        <router-view></router-view>
      </div> -->
      <h2 id="title">{{ title }}</h2>
      <div id="bottomPart">
        <img v-bind:src='work'/>
        <div id="stats">
          <font-awesome-icon class="svg" icon="heart" />{{ appreciations }}
          <font-awesome-icon class="svg" icon="eye" />{{ views }}
        </div>
        <br>
        <div class="columns">
          <div class="column is-1">
            <img class="designerIcon" v-bind:src='designerIcon'/>
          </div>
          <div class="column is-11" id="designerInfo">
            <h3>{{ designer }}</h3>
          <p id="description"> {{ description }}</p></div>
        </div>
        <hr>
         <comments />
      </div>
      <!-- {{ project }} -->
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'

import comments from './comments'
// import './../node_modules/bulma/css/bulma.css'

window.Vue = Vue
export default {
  name: 'project',
  components: {
    'comments': comments
  },
  data () {
    return {
      project: null,
      work: null,
      title: null,
      appreciations: null,
      views: null,
      designer: null,
      designerIcon: null,
      occupation: null,
      description: null
    }
  },
  methods: {
    getDisignerProjects: function (userID) {
      axios
        .get(
          'https://cors-anywhere.herokuapp.com/http://www.behance.net/v2/projects/' +
            userID +
            '?api_key=UhOrt3HySq95LUrfQWErTpR5KK12oq2Q'
        )
        .then(response => {
          this.project = response
          this.work = response.data.project.covers.original
          this.title = response.data.project.name
          this.appreciations = response.data.project.stats.appreciations
          this.views = response.data.project.stats.views
          this.designer = response.data.project.owners[0].display_name
          this.designerIcon = response.data.project.owners[0].images[276]
          this.occupation = response.data.project.owners[0].occupation
          this.description = response.data.project.description
          this.$forceUpdate()
          this.$root.$emit('pageChanged', this.designer + "' s Work")
          console.log(this.project)
        })
        .catch(error => console.log(error.stack))
    }
    // .get("http://api.icndb.com/jokes/random/10")
  },
  mounted () {
    this.getDisignerProjects(this.$route.params.id)
  },
  watch: {
    $route (to, from) {
      if (to.name === 'project') {
        this.$root.$emit('pageChanged', 'PROJECT')
      }
    }
  }
}
</script>
<style scoped>
h2 {
  font-size: 50px;
}
h3{
  font-size: 30px;
}
#project {
  /* margin-top: 20px;
  margin-bottom: 20px; */
  width: 70%;
  margin-right: auto;
  margin-left: auto;
}
#stats {
  text-align: right;
}
#title {
  text-align: center;
  text-transform: capitalize;
  margin: 65px 0;
}
.designerIcon {
  border-radius: 50%;
  height: 60px;
  width: 60px;
}
.column{
  text-align: left;
}
#description{
  font-size: 13px;
}
.arrow-left, .arrow-right{
  text-align: center;
  display: inline;
  font-size: 40px;
  color: #df5563;
}
.arrow{
  color: #df5563;
}
.arrow:hover{
  color: black;
}
.svg{
  margin: 0 10px;
}
hr{
  margin: 40px auto;
  color: #8080801a;
}
/* .arrow-left, .arrow-right .title{
  justify-content: center;
} */
</style>
