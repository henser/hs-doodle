<template>
  <b-card class="card-message mb-4 border-0 shadow-sm text-left">
    <b-card-body class="d-flex flex-column">
      <b-card-text class="d-flex flex-column justify-content-between h-100">
        <p class="text-muted">{{ item.author }}</p>
        <p>{{ item.message }}</p>
        <small class="text-muted">{{ item.timestamp | moment("DD MMM YYYY HH:mm") }}</small>
      </b-card-text>
    </b-card-body>
  </b-card>
</template>

<script>

import Vue from 'vue'
import moment from 'vue-moment'

Vue.use(moment)

export default {
  name: 'Message',
  props: {
    item: Object
  }
}
</script>

<style scoped>
  .card-message {
    width: 90%;
  }

  @media only screen and (min-width: 768px) {
    .card-message {
      width: 66%;
    }
  }
</style>
