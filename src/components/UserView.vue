<template>
  <div class="flex-row">
    <div >
      <img src="https://images.pexels.com/photos/3635300/pexels-photo-3635300.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=400&h=250&fit=crop&crop=focalpoint" alt="">
    </div>
    <div>
      <div>
        <h2>Project Title</h2>
        <p>aqui irá la description</p>
      </div>
    </div>
  </div>

<div class="grid-column">
  <div v-for="project in allProjects" :key="project.title" class="grid-item">
      <img :src="project.image" :alt="project.title">
    </div>
</div>
</template>

<script>
export default {
  name: "UserView",
  props: ['allProjects'],
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

.grid-column{
  display: grid;
  grid-template-columns: repeat(4,1fr);
  width:100%;
}
.grid-item{
  width:15%;
  aspect-ratio: 1;
}
</style>
