<template>
  <footer class="footer bg-dark shadow-sm">
    <div class="container d-flex align-items-center h-100">
      <b-input-group>
        <b-form-input></b-form-input>
        <b-input-group-append>
          <b-button text="Send" variant="success">Send</b-button>
        </b-input-group-append>
      </b-input-group>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      title: process.env.VUE_APP_TITLE
    }
  }
}
</script>

<style scoped>
.footer {
  height: 70px;
  color: #fff;
}

.footer .title {
  font-size: 22px;
  font-weight: bold;
}

a {
  color: #42b983;
}
</style>
