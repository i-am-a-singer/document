<template>
  <section>
    <div class="container is-fluid">
      <div class="container is-fluid">
        <p class="title is-spaced" align="center" style="margin:20px">Try it now!</p>
      </div>
      <div class="container is-fluid" >
        <div class="field has-addons " align="center">
          <p class="control is-large">
            <p class="tag is-light is-medium" type="text" style="text-align:right">{{base_url}}</p>
          </p>
          <p class="control" style="width:60%">
            <input
              class="input is-rounded"
              type="text"
              placeholder="seasons/0/"
              v-model="api_input"
            >
          </p>
          <p class="control">
            <button class="button is-primary is-rounded" v-on:click="request_api">Request</button>
          </p>
        </div>
      </div>
      <div class="field">
        <div class="control">
          <p class="label">Response</p>
          <textarea
            class="textarea is-primary"
            style="height:300px; width:60%; margin-bottom: 100px"
            readonly
          >{{response}}</textarea>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import Vue from "vue";
import Buefy from "buefy";
import "buefy/dist/buefy.css";
const axios = require('axios');

Vue.use(Buefy);


export default {
  data() {
    return {
      number: 0,
      api_input: "",
      response: ""
    };
  },
  methods: {
    request_api() {
      var api = this.api_input
      if (this.api_input == "") api = "seasons/0/"
      axios.get("/singerapi/api/"+api, {
        withCredentials:true,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded',
        },
      }).then(response => {
        if (response.status == "200") {
          this.response = JSON.stringify(response.data, null, 4);
        }
        else {
          this.response = "404 Not Found";
        }
      }).catch(err => {
        this.response = JSON.stringify(err.response.data, null, 4);
      });
    }
  },
  computed: {
    base_url: function() {
      return "/singerapi/api/"
    }
  }
};
</script>
<style scoped>
</style>
