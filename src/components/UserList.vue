<template >
  <div>
    <p class="tasks">
      Users Profile completed:
      {{
        users.filter((user) => {
          return user.done === true;
        }).length
      }}
    </p>
    <p class="pending">
      Pending User Profile:
      {{
        users.filter((user) => {
          return user.done === false;
        }).length
      }}
    </p>
    <user
      v-on:delete-todo="deleteTodo"
      v-on:complete-todo="completeTodo"
      v-bind:key="user"
      v-for="user in users"
      :user.sync="user"
    ></user>
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from "sweetalert";
import User from "./User";

export default {
  props: ["users"],
  components: {
    User,
  },
  methods: {
    deleteTodo(user) {
      sweetalert(
        {
          title: "Are you sure?",
          text: "This User will be permanently deleted!",
          type: "warning",
          showCancelButton: true,
          confirmButtonColor: "#DD6B55",
          confirmButtonText: "Yes, delete it!",
          closeOnConfirm: false,
        },
        () => {
          const todoIndex = this.users.indexOf(user);
          this.users.splice(todoIndex, 1);
          sweetalert("Deleted!", "Your User has been deleted.", "success");
        }
      );
    },
    completeTodo(user) {
      const todoIndex = this.users.indexOf(user);
      this.users[todoIndex].done = true;
      sweetalert("Success!", "Profile Completed!", "success");
    },
  },
};
</script>

<style scoped>
p.tasks {
  margin: 1%;
  text-align: left;
  color: green;
  background-color: aquamarine;
  font-family: Georgia, "Times New Roman", Times, serif;
  font-size: 20px;
  font-weight: bold;
}
p.pending {
  margin: 1%;
  background-color: silver;
  text-align: left;
  color: #660033;
  font-family: Georgia, "Times New Roman", Times, serif;
  font-size: 20px;
  font-weight: bold;
}
</style>

