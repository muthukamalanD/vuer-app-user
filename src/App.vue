<template>
  <div style="background-color: #F5F5F5" id="app">
    <h1
      style="
        color: maroon;
        background-color: #66CCFF;
        margin: 1%;
        font-family: times;
      "
      class="ui dividing centered header"
    >
      USERS DATA
    </h1>
    <div class="ui three row centered grid">
      <div class="column">
        <create-user v-on:create-todo="createTodo"></create-user>
        <user-list style="color: black" v-bind:users="users"></user-list>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from "sweetalert";
import UserList from "./components/UserList";
import CreateUser from "./components/CreateUser";

export default {
  name: "app",
  components: {
    UserList,
    CreateUser,
  },
  data() {
    return {
      users: [
        {
          name: "USER 1",
          phone: "939493949",
          email: "user1@email.com",
          address: "1 st street,annanagar,chennai",
          done: false,
        },
        {
          name: "USER 2",
          phone: "9341343234",
          email: "user1@email.com",
          address: "2 nd  street,velacherry,chennai",
          done: true,
        },
        {
          name: "USER 3",
          phone: "9323544354",
          email: "user1@email.com",
          address: "3 rd street,guindy,chennai",
          done: false,
        },
        {
          name: "USER 4",
          phone: "9847474763",
          email: "user1@email.com",
          address: "4 th street,thoraipakkam,chennai",
          done: false,
        },
      ],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.users.push(newTodo);
      sweetalert("Success!", "User created!", "success");
    },
  },
};
</script>