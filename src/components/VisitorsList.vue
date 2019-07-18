<template>
  <div>
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
        <transition-group>
          <tr v-for="user in users" v-bind:key="user.id">
            <th scope="row">{{user.name}}</th>
            <td>{{user.email}}</td>
            <td>{{user.address}}</td>
            <td>{{user.comment}}</td>
            <td>
              <div>
                <b-button class="btn-style" @click="$emit('onEdit', user.id)" variant="warning">Edit</b-button>
                <b-button
                  @click="$emit('onDelete', user.id)"
                  class="btn-style"
                  variant="danger"
                >Delete</b-button>
              </div>
            </td>
          </tr>
        </transition-group>
      </tbody>
    </table>
  </div>
</template>

<script>
// import EditModal from "./EditModal";
export default {
  name: "VisitorsList",
  //   components: { EditModal },
  props: ["users"],
  data() {
    return {};
  },
  methods: {
    // onEdit(id) {
    //   const finder = this.user.map(e => e.id);
    //   console.log(finder);
    // },
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
</style>

