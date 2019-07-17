<template>
  <div>
    <EditModal />
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
        <tr v-for="uses in user" v-bind:key="uses.id">
          <th scope="row">{{uses.name}}</th>
          <td>{{uses.email}}</td>
          <td>{{uses.address}}</td>
          <td>{{uses.comment}}</td>
          <td>
            <div>
              <b-button class="btn-style" variant="warning">Edit</b-button>
              <b-button
                @click="$emit('onDelete', uses.id)"
                class="btn-style"
                variant="danger"
              >Delete</b-button>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import EditModal from "./EditModal";
export default {
  name: "Header",
  components: { EditModal },
  props: ["user"],
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
</style>

