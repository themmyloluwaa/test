<template>
  <div class="addvisitor">
    <b-form @submit="onSubmit" class="text-center w-50 addvisitor">
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
      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddVisitors",
  props: ["editUser"],
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
      const inputData = {
        id: uuid.v4(),
        name: this.form.name,
        email: this.form.email,
        address: this.form.address,
        comment: this.form.comment
      };
      this.$emit("add-user", inputData);
      this.form.name = "";
      this.form.email = "";
      this.form.address = "";
      this.form.comment = "";
    }
  }
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.addvisitor {
  margin: 0 auto;
  margin-top: 20px;
}
</style>
