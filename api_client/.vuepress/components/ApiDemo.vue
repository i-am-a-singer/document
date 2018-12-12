<template>
  <section>
    <div class="container is-fluid">
      <div class="field has-addons">
        <p class="control is-large">
          <code>{{base_url}}/singerapi/api/</code>
        </p>
        <p class="control">
          <input class="input" type="text" placeholder="season/1/">
        </p>
        <p class="control">
          <button class="button is-primary">Request</button>
        </p>
      </div>
      <div class="field">
        <div class="control">
          <textarea class="textarea is-primary" readonly></textarea>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import Vue from "vue";
import Buefy from "buefy";
import "buefy/dist/buefy.css";
Vue.use(Buefy);
export default {
  data() {
    return {
      number: 0,
      base_url: window.location.protocol + "://" + window.location.host
    };
  },
  methods: {
    increment() {
      if (this.number >= 0) {
        this.number++;
      }
    },
    decrement() {
      if (this.number > 0) {
        this.number--;
      }
    }
  }
};
</script>
<style scoped>
</style>
