<template>
  <div>
    <h2>ADD NEW PROJECT</h2>
  </div>
  <form @submit.prevent="handleSubmit">
    <div class="flex-row">
      <div class="flex-column">
        <label for="title">Project Title</label>
        <input v-model="title" type="text" />
      </div>
      <div class="flex-column">
        <label for="image">Image Url</label>
        <input v-model="image" type="url" />
      </div>
    </div>
    <div class="flex-column">
      <label for="description">Description</label>
      <textarea v-model="description" name="description" id="description"></textarea>
    </div>
    <div>
      <button>Add</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "AdminView",
  emits: ["createProject"],//preguntar a Andres - si hay elementos fuera del form sale un error en la consola que se soluciona generando un emit aqui
  data() {
    return {
      title: "",
      image: "",
      description: ""
    };
  },
  methods: {
    handleSubmit() {
      const newProject = {
        title: this.title,
        image: this.image,
        description: this.description
      };

      this.$emit("createProject", newProject);
      this.reset()
    },
    reset() {
      this.title = ''
      this.image = ''
      this.description = ''
    }
  }
};
</script>

<style>
.flex-row {
  display: flex;
  flex-direction: row;
  width: 100%;
  gap: 8px;
  padding-bottom: 8px;
}

.flex-column {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 8px;
  padding-bottom: 8px;
}
</style>
