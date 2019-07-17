<template>
  <div id="app">
    <h1 class="h1">Ehealth4Everyone Attendance App</h1>
    <AddVisitors v-on:add-user="addUser" />
    <Header v-bind:user="userInfo" class="header" v-on:onDelete="deleteData" />
    <!-- <EditModal v:bind:edituser="userInfo" /> -->
    <!-- <vue-particles
      id="particles"
      color="#2c1b40"
      :lineLinked="false"
      :linesDistance="0"
      :hoverEffect="false"
    ></vue-particles>-->
  </div>
</template>

<script>
import AddVisitors from "./components/AddVisitors.vue";
import Header from "./components/Header";
// import EditModal from "./components/EditModal";
export default {
  name: "app",
  components: { Header, AddVisitors },
  data() {
    return {
      userInfo: []
    };
  },
  methods: {
    addUser(inputData) {
      this.userInfo = [...this.userInfo, inputData];
    },
    deleteData(id) {
      this.userInfo = this.userInfo.filter(e => e.id !== id);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  line-height: 1.4;
  /* overflow-y: hidden; */
}
#app {
  /* background-color: #013033; */
  min-height: 100vh;
  scroll-behavior: none;
}
.h1 {
  text-align: center;
  margin: 20px 0;
}

@media screen and (max-width: 400px) {
  #app {
    font-size: 15px;
  }
}
</style>
