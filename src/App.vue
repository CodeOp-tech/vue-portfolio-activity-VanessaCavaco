<template>
  <div class="buttons">
    <button :class="{ activeButton: isAdmin }" @click="isAdmin = true">ADMIN</button>
    <button :class="{ activeButton: !isAdmin }" @click="isAdmin = false">USER</button>
  </div>

  <div>
    <h1>MY PORTFOLIO</h1>
  </div>
  
  <div class="grid-component">
    <admin-view v-if="isAdmin" @createProject="addProject"/>
    <user-view v-else :allProjects = "allProjects" /> 
  </div>
</template>

<script>
import AdminView from "./components/AdminView.vue";
import UserView from "./components/UserView.vue";

export default {
  name: "app",
  components: {
    userView: UserView,
    adminView: AdminView
  },
  data() {
    return {
      isAdmin: true,
      allProjects: [],
    };
  },
  methods: {
    addProject(newProject) {
      this.allProjects.push(newProject);
      console.log ("pepu", this.allProjects)
    }
  }
};
</script>

<style>
body{
  display: grid;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  width: 75%;
  margin: auto;
}
h1{
  text-align: center;
}
.activeButton {
  background-color: red;
}
.buttons{
  display: flex;
  justify-content: end;
}
.grid-component{
  display: grid;
  justify-items: center;
}
</style>
