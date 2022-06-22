<template>
  <div class="d-flex justify-content-center align-items-center">
    <div class="card" style="width: 30rem">
      <img :src="imageUrl" class="card-img-top" alt="user image" width="200" />
      <div class="card-body">
        <h5 class="card-title">{{ user.name }}</h5>
        <p class="card-text">
          {{ user.email }}
        </p>
        <a class="btn btn-secondary" @click="goBack">Go Back</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      required: true,
    },
  },

  data() {
    return {
      imageUrl: null,
    };
  },

  methods: {
    async getImageUrl() {
      const res = await fetch(
        `https://jsonplaceholder.typicode.com/photos/${this.user.id}/`
      );
      const data = await res.json();
      console.log(data.url);
      return data.url;
    },

    goBack() {
      this.$emit("back");
    },
  },

  async mounted() {
    this.imageUrl = await this.getImageUrl();
  },
};
</script>

<style></style>
