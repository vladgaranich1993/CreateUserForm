<template>
  <div id="app">
    <Form @addUser="addUser"/>
    <Table :users="users"/>
  </div>
</template>

<script>
import Form from "./components/Form";
import Table from "./components/Table";

export default {
  name: "App",
  data() {
    return {
      users: [{id:1,name:'Harry',surname:'Potter',emailAddress:'hpotter@gmail.at'}]
    };
  },
  components: {
    Form,
    Table
  },
  methods: {
    addUser(newUser) {
      this.users.push(newUser);
    }
  }
};
</script>

<style>
</style>
