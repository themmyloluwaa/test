<template>
  <div id="simpleModal" class="modal">
    <b-form @submit="onSubmit" @reset="onReset" class="modal-content">
      <b-form-group id="input-group-1" label="Your Name:" label-for="input-1">
        <b-form-input
          id="input-1"
          maxlength="30"
          v-model="form.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="input-group-2"
        label="Email address:"
        label-for="input-2"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-2"
          v-model="form.email"
          type="email"
          required
          placeholder="Enter email"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Your Address:" label-for="input-3">
        <b-form-input
          maxlength="50"
          id="input-3"
          v-model="form.address"
          required
          placeholder="Enter Address"
        ></b-form-input>
      </b-form-group>
      <b-form-group id="input-group-4" label="Leave any comment:" label-for="input-4">
        <b-form-textarea
          id="textarea"
          v-model="form.comment"
          placeholder="Comment..."
          rows="3"
          max-rows="6"
          maxlength="50"
        ></b-form-textarea>
      </b-form-group>
      <b-button @click="Save" class="btn-style" variant="warning">Edit</b-button>
      <b-button @click="Cancel" class="btn-style" variant="danger">Delete</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  name: "EditModal",
  props: ["edituser"],
  data() {
    return {
      form: {
        name: "",
        email: "",
        address: "",
        comment: ""
      },
      isShow: false
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(evt) {
      evt.preventDefault();
      // Reset our form values
      this.form.email = this.form.name = "";
      this.form.food = null;

      // Trick to reset/clear native browser form validation state
      this.show = false;
      this.$nextTick(() => {
        this.show = true;
      });
    }
  }
};
</script>
<style scoped>
.hide {
  display: none;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.5);
}
.show {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.5);
}
.modal-content {
  background-color: #f4f4f4;
  margin: 20% auto;
  padding: 20px;
  width: 80%;
  box-shadow: 0 5px 8px 0 rgba(0, 0, 0, 0.3), 0 7px 20px 0 rgba(0, 0, 0, 0.17);
}
.closeBtn {
  color: #ccc;
  float: right;
  font-size: 30px;
}
.closeBtn:hover,
.closeBtn:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
</style>
