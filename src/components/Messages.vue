<template>
  <div class="messages">
    <!-- Start: Infinite Loading-->
    <infinite-loading direction="top" :identifier="infiniteId" @infinite="infiniteHandler"></infinite-loading>
    <!-- End: Infinite Loading-->
    <section class="section">
      <!-- Start: Card -->
      <div class="container">
        <div class="row" v-show="this.processing">
          <div v-for="(item, $index) in limit" :key="$index" class="col-12 d-flex h-auto">
            <message-placeholder></message-placeholder>
          </div>
        </div>
        <div class="row">
          <div v-for="(item, $index) in list" :key="$index" class="col-12 d-flex h-auto" v-bind:class="[ item.author === 'henser' ? 'justify-content-end' : '']">
            <message :item="item"></message>
          </div>
        </div>
      </div>
      <!-- End: Card -->
    </section>
    <footer class="footer w-100 bg-dark shadow-sm" @keydown.enter="postMessage">
      <div class="container d-flex align-items-center h-100">
        <b-input-group>
          <b-form-input type="text" v-model="user.message"></b-form-input>
          <b-input-group-append>
            <b-button text="Send" variant="success" @click="postMessage">Send</b-button>
          </b-input-group-append>
        </b-input-group>
      </div>
    </footer>
  </div>
</template>

<script>

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
import InfiniteLoading from 'vue-infinite-loading'

import Message from './Message'
import MessagePlaceholder from './MessagePlaceholder'

Vue.use(VueAxios, axios)

export default {
  name: 'Messages',
  components: {
    InfiniteLoading,
    Message,
    MessagePlaceholder
  },
  data () {
    return {
      limit: 6,
      processing: false,
      complete:  false,
      list: [],
      timestamp: 0,
      user: {
        author: 'henser',
        message: ''
      },
      infiniteId: +new Date()
    }
  },
  methods: {
    infiniteHandler ($state) {

      if (this.processing) {
        return;
      }

      this.processing = true;

      axios.get(process.env.VUE_APP_API_PATH, {
        params: {
          token: process.env.VUE_APP_API_TOKEN,
          since: this.timestamp,
          limit: this.limit
        },
      }).then(({data}) => {

        if (data.length) {
          this.timestamp = data[data.length - 1]['timestamp'];
          this.list.unshift(...data.reverse());
          $state.loaded();
          this.complete = false;
        } else {
          $state.complete();
          this.complete = true;
        }

        this.processing = false;
      });
    },

    postMessage() {

      if (this.user.message) {
        axios.post(process.env.VUE_APP_API_PATH, {
          'message': this.user.message,
          'author': this.user.author
        },{
          headers: {
            'Content-Type': 'application/json',
            'token': process.env.VUE_APP_API_TOKEN,
          }
        })
        .then(() => {

          // because the API isn't returning data in reverse chronological order,
          // there isn't much to be done here besides updating the inifite load
          // if working properly, the data in the request response would be used
          // to immediately place the message in the view
          if (this.complete) {
            this.infiniteId ++;
          }

          this.user.message = '';
        });
      }
    }
  }
}
</script>

<style scoped>

a {
  color: #42b983;
}

.messages {
  background-image: url("../assets/bg.png");
  background-repeat: repeat;
  background-color: #fafafa;
  padding-top: 30px;
}

.messages .justify-content-end .card-message {
  background-color: #fcf6c4;
  text-align: right;
}

.footer {
  position: sticky;
  bottom: 0;
  left: 0;
  height: 70px;
  color: #fff;
}

.footer .title {
  font-size: 22px;
  font-weight: bold;
}

</style>
