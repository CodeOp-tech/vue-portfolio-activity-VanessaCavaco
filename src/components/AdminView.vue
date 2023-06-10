<template>
  <div>
    <h2>ADD NEW PROJECT</h2>
  </div>
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
    <button @click="handleSubmit">Add</button>
  </div>
</template>

<script>
export default {
  name: "AdminView",
  data() {
    return {
      title: "",
      image: "https://images.pexels.com/photos/2400594/pexels-photo-2400594.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=400&h=250&fit=crop&crop=focalpoint",
      description: ""
    };
  },
  methods: {
    handleSubmit() {
      const project = {
        title: this.title,
        image: this.image,
        description: this.description
      };

      this.$emit("createProject", project);
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
.flex-row{
  display: flex;
  flex-direction: row;
  width: 100%;
  gap: 8px;
  padding-bottom: 8px;
}
.flex-column{
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 8px;
  padding-bottom: 8px;
}
</style>
