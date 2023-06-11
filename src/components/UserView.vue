<template>
  <div :class="{visible: active, hidden: !active}"  class="flex-row">
    <div>
      <img :src="image" :alt="description" class="img-big">
    </div>
    <div>
      <div>
        <h2>{{ title }}</h2>
        <p>{{description}}</p>
      </div>
    </div>
  </div>

<div class="grid-column">
  <div v-for="(project,index) in allProjects" :key="index" class="grid-item" @click="showProject">
      <img :src="project.image" :alt="project.title" :id="index" class="grid-item">
    </div>
</div>
</template>

<script>
export default {
  name: "UserView",
  props: ['allProjects'],

  data(){
    return{
      active:false,
      title: "",
      image: "",
      description:"",
    }
  },
  
  methods: {
    showProject(event){
      //console.log("pepita", event.target.src)
      const imageId = event.target.id
      this.title = this.allProjects[imageId].title
      this.image = this.allProjects[imageId].image
      this.description = this.allProjects[imageId].description
      this.active = true;
    },
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

.grid-column{
  display: grid;
  grid-template-columns: repeat(4,1fr);
  width:100%;
}
.grid-item{
  width: 100%;
  aspect-ratio: 1;
}
.img-big{
  width: 100%;
  aspect-ratio: 1;
}
.hidden{
  visibility: hidden;
}
.visible{
  visibility: visible;
}
</style>
