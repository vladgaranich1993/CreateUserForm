<template>
  <form @submit.prevent="addUser">
    <input required v-model="name" type="text" placeholder="First Name">
    <input required v-model="surname" type="text" placeholder="Last Name">
    <button type="submit">Submit</button>
  </form>
</template>
<script>
const domain = "@gmail.at";
export default {
  data() {
    return {
      name: "",
      surname: ""
    };
  },
  methods: {
    getFormattedName() {
      return this.name
        .split(" ")
        .join("")
        .charAt(0)
        .toLowerCase();
    },
    getFormattedSurName() {
      return this.surname
        .split(" ")
        .join("")
        .toLowerCase();
    },
    addUser() {
      const newUser = {
        id: Date.now(),
        name: this.name,
        surname: this.surname,
        emailAddress: `${this.getFormattedName()}${this.getFormattedSurName()}${domain}`
      };

      this.$emit("addUser", newUser);
      this.name = "";
      this.surname = "";
    }
  }
};
</script>
<style>
    form {
    width: 750px;
    border-collapse: collapse;
    margin: 10px auto;
    }
</style>
