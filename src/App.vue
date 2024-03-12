<!-- Composition API -->
<!-- <script setup>
import { ref } from "vue";

const data = ref({
  firstName: "John",
  lastName: "Doe",
  email: "john@gmail.com",
  gender: "male",
  picture: "https://randomuser.me/api/portraits/men/10.jpg",
});
const getUser = async () => {
  let res = await fetch("https://randomuser.me/api");
  let { results } = await res.json();
  data.value.firstName = results[0]?.name?.first;
  data.value.lastName = results[0]?.name?.last;
  data.value.email = results[0]?.email;
  data.value.gender = results[0]?.gender;
  data.value.picture = results[0]?.picture?.large;
};
</script> -->

<!-- Options API -->
<script>
export default {
  data() {
    return {
      data: {
        firstName: "John",
        lastName: "Doe",
        email: "john@gmail.com",
        gender: "male",
        picture: "https://randomuser.me/api/portraits/men/10.jpg",
      },
    };
  },
  methods: {
    async getUser() {
      let res = await fetch("https://randomuser.me/api");
      let { results } = await res.json();
      this.data.firstName = results[0]?.name?.first;
      this.data.lastName = results[0]?.name?.last;
      this.data.email = results[0]?.email;
      this.data.gender = results[0]?.gender;
      this.data.picture = results[0]?.picture?.large;
    },
  },
};
</script>

<template>
  <main>
    <img
      v-bind:src="data.picture"
      :alt="`${data.firstName} ${data.lastName}`"
      :class="data.gender"
    />
    <h1>{{ data.firstName }} {{ data.lastName }}</h1>
    <h3>Email: {{ data.email }}</h3>
    <button :class="data.gender" @click="getUser()">Get Random User</button>
  </main>
</template>
