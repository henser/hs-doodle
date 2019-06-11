<template>
  <div class="col-12 d-flex h-auto">
    <b-card class="card-placeholder mb-4 border-0 shadow-sm mx-4 text-left">
      <b-card-footer class="bg-white border-0">
        <p class="card-placeholder__content w-50"></p>
        <p class="card-placeholder__content w-100"></p>
        <p class="card-placeholder__content w-25"></p>
      </b-card-footer>
    </b-card>
  </div>
</template>

<script>
export default {
  name: 'MessagePlaceholder'
}
</script>

<style scoped>

.card-placeholder__content {
  display: block;
  border-radius: none;
  animation: pulse 1s infinite ease-in-out;
  height: 20px;
  margin: 10px 0;
}

.card-placeholder {
  width: 80%;
}

@media only screen and (min-width: 768px) {
  .card-placeholder {
    width: 50%;
  }
}

@keyframes pulse {
    0% {
        background-color: rgba(165, 165, 165, 0.1);
    }
    50% {
        background-color: rgba(165, 165, 165, 0.3);
    }
    100% {
        background-color: rgba(165, 165, 165, 0.1);
    }
}
</style>
