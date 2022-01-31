<template>
  <div style="font-weight:bold;font-size:18px" class="ui centered card">
    <div style="background-color:#FFC300" class="content" v-show="!isEditing">
      <div style="margin-bottom:10px;color:#660099" class="header">
       <i class='user icon'></i> {{ user.name }}
      </div>
      <div style="font-size:15px" class="meta">
       <li> {{ user.phone }}</li>
      </div>
      <div style="font-size:15px"  class="meta">
       <li> {{ user.email }}</li>
      </div>
      <div style="font-size:15px"  class="meta">
        <li>{{ user.address }}</li>
      </div>
      <div style="margin-top:35px;" class="extra content">
        <span style="color:maroon" class="right floated edit icon" v-on:click="showForm">
          Update<i class="edit icon"></i>
        </span>
        <span style="color:maroon" class="right floated trash icon" v-on:click="deleteTodo(user)">
         Delete <i class="trash icon"></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>User Name:</label>
          <input type="text" v-model="user.name" />
        </div>
        <div class="field">
          <label>Phone No:</label>
          <input type="text" v-model="user.phone" />
        </div>
        <div class="field">
          <label>Email</label>
          <input type="text" v-model="user.email" />
        </div>
        <div class="field">
          <label>Address</label>
          <input type="text" v-model="user.address" />
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" v-on:click="hideForm">
            UPDATE
          </button>
        </div>
      </div>
    </div>
    <div
      class="ui bottom attached green basic button"
      v-show="!isEditing && user.done"
      disabled
    >
                      User Profile Completed
    </div>
    <div
      class="ui bottom attached red basic button"
      v-on:click="completeTodo(user)"
      v-show="!isEditing && !user.done"
    >
     User Profile Pending
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: ["user"],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    completeTodo(user) {
      this.$emit("complete-todo", user);
    },
    deleteTodo(user) {
      this.$emit("delete-todo", user);
    },
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
  },
};
</script>
