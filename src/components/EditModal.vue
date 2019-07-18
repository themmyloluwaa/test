<template>
  <div class="modal">
    <div class="modal-content">
      <span class="closeBtn">&times;</span>
      <b-form>
        <b-form-group id="input-group-1" @submit="onSubmit" label="Your Name:" label-for="input-1">
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
        <b-button class="btn-style" variant="warning">Update</b-button>
        <b-button class="btn-style" variant="danger" @click="$emit('cancelModal', user.id)">Cancel</b-button>
      </b-form>
    </div>
  </div>
</template>

<script>
export default {
  name: "EditModal",
  props: ["user"],
  data() {
    return {
      form: {
        name: "",
        email: "",
        address: "",
        comment: ""
      }
    };
  },

  methods: {
    onSubmit(evt) {
      evt.preventDefault();
    }
  }
};
</script>
<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.5);
  display: block;
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
  text-emphasis: right;
}
.closeBtn:hover,
.closeBtn:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
</style>
