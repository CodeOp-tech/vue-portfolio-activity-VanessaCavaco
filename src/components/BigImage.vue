<template>
    <div   class="flex-row">
      <div>
        <img :src="bigProject.image" :alt="bigProject.description" class="img-big">
      </div>
      <div>
        <div>
          <h2>{{ bigProject.title }}</h2>
          <p>{{ bigProject.description}}</p>
        </div>
      </div>
    </div>

  </template>
  
  <script>
  export default {
    name: "BigImage",
    props:["bigProject"]
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
  .grid-item:hover{
  transform: scale(1.02);
  }
  .img-big{
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
    border-radius: 20%;
    box-shadow:  10px 10px 5px 0px rgba(0,0,0,0.75);
  }
  
  </style>
  