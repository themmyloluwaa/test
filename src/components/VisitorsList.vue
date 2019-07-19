<template>
  <div>
    <div v-for="(user, i) in users" v-bind:key="user.id">
      <div class="modal" v-show="!show">
        <div class="modal-content">
          <span class="closeBtn">&times;</span>
          <b-form>
            <b-form-group id="input-group-1" label="Your Name:" label-for="input-1">
              <b-form-input
                id="input-1"
                maxlength="30"
                v-model="user.name"
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
                v-model="user.email"
                type="email"
                required
                placeholder="Enter email"
              ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-3" label="Your Address:" label-for="input-3">
              <b-form-input
                maxlength="50"
                id="input-3"
                v-model="user.address"
                required
                placeholder="Enter Address"
              ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-4" label="Leave any comment:" label-for="input-4">
              <b-form-textarea
                id="textarea"
                v-model="user.comment"
                placeholder="Comment..."
                rows="3"
                max-rows="6"
                maxlength="50"
              ></b-form-textarea>
            </b-form-group>
            <b-button class="btn-style" nvariant="warning" @click="reRender(user,false,i)">Update</b-button>
            <b-button class="btn-style" @click="show= true" variant="danger">Cancel</b-button>
          </b-form>
        </div>
      </div>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
            <th scope="col">Address</th>
            <th scope="col">Comment</th>
            <th scope="col">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">{{user.name}}</th>
            <td>{{user.email}}</td>
            <td>{{user.address}}</td>
            <td>{{user.comment}}</td>
            <td>
              <div>
                <b-button class="btn-style" @click="show = !show" variant="warning">Edit</b-button>
                <b-button
                  @click="$emit('onDelete', user.id)"
                  class="btn-style"
                  variant="danger"
                >Delete</b-button>
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
// import EditModal from "./EditModal";
export default {
  name: "VisitorsList",
  //   components: { EditModal },
  props: ["users"],
  data() {
    return {
      show: null
    };
  },
  methods: {
    reRender(user, state, i) {
      this.show[i] = state;
      //Make it rerender
      user.id += 100;
    }
  },
  created() {
    //Set status to an array with the length of users
    this.show = new Array(this.$props.length).fill(false);
  },
  computed: {
    userss() {
      //Get the user from props, so that we can watch for it
      return this.$props.user;
    }
  },
  watch: {
    userss() {
      //Anytime a new user is created, push false to the array
      this.show.push(false);
    }
  }
};
</script>

<style scoped>
@import url("https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.css");
table {
  border: 1px solid black;
  border-radius: 1em;
  table-layout: fixed;
  width: 80vw;
  margin: 0 auto;
  background: #2c1b40;
  color: #fff;
  overflow: hidden;
  margin-top: 20px;
}

th,
td {
  border: 1px solid black;
  min-width: 100px;
  overflow: hidden;
  word-wrap: break-word;
  font-size: 0.8em;
}
thead {
  font-size: 1.5em;
  text-align: center;
}

.btn-style {
  margin: 0 10px;
}
/* .v-enter-active {
  animation: bounceIn 2s;
} */
tbody {
  animation: bounceIn 5s;
  animation: bounceIn 2s reverse;
}
/* .v-leave-active {
  animation: bounceIn 2s reverse;
} */
@keyframes bounceIn {
  0%,
  100% {
    transform: scale(0.1);
    opacity: 0;
  }
  50% {
    transform: scale(2);
    opacity: 1;
  }
}
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

