<template>
  <div id="">
    <User :users="users" @details="getDetails" v-if="!showDetails" />
    <Details :user="currentUser" @back="goBack" v-else />
  </div>
</template>

<script>
import User from "./components/Users.vue";
import Details from "./components/Details.vue";
export default {
  name: "App",
  components: {
    User,
    Details,
  },
  data() {
    return {
      users: [],
      showDetails: false,
      currentUser: {},
    };
  },

  methods: {
    async getUser() {
      try {
        let res = await fetch("https://jsonplaceholder.typicode.com/users/");
        return await res.json();
      } catch {
        console.log("unable to get data");
      }
    },
    getDetails(id) {
      const match = this.users.filter((e) => e.id == id);
      if (match.length) {
        this.showDetails = true;
        this.currentUser = match[0];
      }
    },
    goBack(id) {
      this.showDetails = false;
      this.currentUser = null;
    },
  },

  async mounted() {
    this.users = await this.getUser();
  },
};
</script>

<style></style>
