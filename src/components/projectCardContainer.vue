<template>
  <div id="projectCardContainer">
fvfbfg
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
window.Vue = Vue
export default {
  name: 'projectCardContainer',
  data () {
    return {
      designer: null,
      collection: null
    }
  },
  methods: {
    getDisignerProjects: function (userID) {
      axios
        .get(
          'https://cors-anywhere.herokuapp.com/http://www.behance.net/v2/users/user/collections' +
            userID +
            '?api_key=UhOrt3HySq95LUrfQWErTpR5KK12oq2Q'
        )
        .then(response => {
          this.project = response
          
          this.$forceUpdate()
          console.log(this.project)
        })
        .catch(error => console.log(error.stack))
    }
    // .get("http://api.icndb.com/jokes/random/10")
  },
  mounted () {
    this.getDisignerProjects('TSabe')
    this.getDisignerProjects('TSabe')
    this.getDisignerProjects('TSabe')
    this.getDisignerProjects('TSabe')
  }
}
</script>