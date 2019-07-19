<template>
  <div id="app">
    <h1 class="h1">Ehealth4Everyone Attendance App</h1>
    <AddVisitors v-on:add-user="addUser" />
    <VisitorsList v-bind:users="userInfo" class="header" v-on:onDelete="deleteUser" />
    <!-- <edit-modal :user="current" v-show="isEditing" v-on:cancelModal="cancelModal" /> -->
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
import VisitorsList from "./components/VisitorsList";
// import EditModal from "./components/EditModal";
export default {
  name: "app",
  components: { VisitorsList, AddVisitors },
  data() {
    return {
      userInfo: [],
      // isEditing: false,
      current: {}
    };
  },
  methods: {
    addUser(inputData) {
      this.userInfo = [...this.userInfo, inputData];
    },
    deleteUser(id) {
      this.userInfo = this.userInfo.filter(e => e.id !== id);
    }
    // editUser(id) {
    //   this.userInfo = this.userInfo.forEach(user => {
    //     if (user.id === id) {
    //       this.current = user;
    //       this.isEditing = true;
    //     }
    //   });
    // }
    // cancelModal(id) {
    //   // console.log(this);
    //   let $vm = this;
    //   console.log($vm.userInfo);
    //   console.log($vm);
    //   return () => {
    //     $vm.userInfo = $vm.userInfo.forEach(user => {
    //       if (user.id === id) {
    //         $vm.current = user;
    //         $vm.isEditing = false;
    //       }
    //     });
    // };
    // }
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
