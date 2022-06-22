<template>
  <div class="">
    <div class="bg-success py-5 mb-3"></div>
    <div class="container">
      <div class="row">
        <div v-for="user in users" :key="user.id" class="col-3 py-2">
          <div class="card" style="width: 18rem">
            <div class="card-body">
              <!-- <div class="text-center">
                <i class="fa-solid fa-user fa-2x"></i>
              </div> -->
              <h5 class="card-title">
                <i class="fa-solid fa-user fa-1x pe-3"></i> {{ user.name }}
              </h5>
              <p class="card-text">{{ user.email }}</p>

              <button class="btn btn-success" @click="viewDetails(user.id)">
                View Detail
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    users: {
      requird: true,
    },
  },

  methods: {
    viewDetails(id) {
      this.$emit("details", id);
    },
  },
};
</script>

<style></style>
