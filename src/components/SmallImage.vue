<template>

    <div class="grid-item" @click="handleClick">
        <img 
        :src="project.image" :alt="project.title" class="grid-item">
    </div>
  </template>
  
  <script>
  export default {
    name: 'SmallImage',
    props: ["project"],
    methods:{
      handleClick(){
        this.$emit('bigImage',{
          title:this.project.title,
          image:this.project.image,
          description:this.project.descrption,
        })
      }
    }
  };
  </script>
  
  <style>
  
  .grid-item{
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
    border-radius: 20%;
    
    cursor: pointer;
    transition: all 0.2s ease-in-out;
  }
  .grid-item:hover{
  transform: scale(1.02);
  }  
  </style>