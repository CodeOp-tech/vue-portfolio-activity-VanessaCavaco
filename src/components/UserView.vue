<template>
  <!--
  <div v-if="project !== null"  class="flex-row">
    <div>
      <img :src="project.image" :alt="project.description" class="img-big">
    </div>
    <div>
      <div>
        <h2>{{ project.title }}</h2>
        <p>{{ project.description}}</p>
      </div>
    </div>
  </div>

<div v-if="allProjects.length>0" class="grid-column">
  <div v-for="(project,index) in allProjects" :key="index" class="grid-item" @click="showProject(project)">
      <img :src="project.image" :alt="project.title" :id="index" class="grid-item">
  </div>
</div>
-->


<div v-if="bigProject !== null">
  <big-image :bigProject="bigProject" class="img-big"/>
</div>

<div class="flex-row">
  <div v-if = "allProjects.length > 0" class="grid-column">
    <small-image v-for="(project,index) in allProjects" :key="index" :project="project" @bigImage="addBigProject(bigProject)" class="grid-item"/> 
  </div>
</div> 
</template>

<script>
import SmallImage from "./smallImage.vue";
import BigImage from "./BigImage.vue";

export default {
  name: "UserView",
  components:{
    smallImage: SmallImage,
    bigImage: BigImage,
  },
  props: ["allProjects"],
  
  data(){
    return{
    bigProject:null,
    }
  },
  methods:{
    addBigProject(bigProject){
      this.bigProject = bigProject;
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
  
  .grid-column{
    display: grid;
    grid-template-columns: repeat(4,1fr);
    width:100%;
    gap:16px;
  }
  .grid-item{
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
    border-radius: 20%;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
  }

.img-big{
  width: 100%;
  aspect-ratio: 1;
  object-fit: cover;
  border-radius: 20%;
  box-shadow:  10px 10px 5px 0px rgba(0,0,0,0.75);
}

</style>
