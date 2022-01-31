<template>
  <div class="ui basic content right aligned segment">
    <button
      class="ui basic button icon"
      v-on:click="openForm"
      v-show="!isCreating"
    >CREATE USER
      <i class="plus icon"></i>
    </button>
    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <div class="ui form">
          <div class="field">
            <label>USER NAME</label>
            <input v-model="nameText" type="text" />
          </div>
          <div class="field">
            <label>PHONE NUMBER</label>
            <input v-model="phoneNumber" type="text" />
          </div>
          <div class="field">
            <label>EMAIL</label>
            <input v-model="emailId" type="text" />
          </div>
          <div class="field">
            <label>ADDRESS</label>
            <input v-model="addressText" type="text" />
          </div>
          <div class="ui two button attached buttons">
            <button class="ui basic blue button" v-on:click="sendForm()">
              Create
            </button>
            <button class="ui basic red button" v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nameText: "",
      phoneNumber: "",
      emailId: "",
      addressText: "",
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (
        this.nameText.length > 0 &&
        this.phoneNumber.length > 0 &&
        this.emailId.length > 0 &&
        this.addressText.length > 0
      ) {
        const name = this.nameText;
        const phone = this.phoneNumber;
        const email = this.emailId;
        const address = this.addressText;
        this.$emit("create-todo", {
          name,
          phone,
          email,
          address,
          done: false,
        });
        this.nameText = "";
        this.phoneNumber = "";
        this.emailId = "";
        this.addressText = "";
        this.isCreating = false;
      }
    },
  },
};
</script>
