<template>
    <div class="sidebar">
      <ul>
        <li 
          v-for="item in items" 
          :key="item.id" 
          :class="['sidebar-item', { active: activeItem === item.id }]" 
          @click="setActive(item.id)"
        >
          {{ item.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        items: [
          { id: 1, name: 'Home' },
          { id: 2, name: 'About' },
          { id: 3, name: 'Contact' },
          { id: 4, name: 'Gallary' },
        ],
        activeItem: 3, // Default active item
      };
    },
    methods: {
      setActive(itemId) {
        this.activeItem = itemId;
      },
    },
  };
  </script>
  
  <style scoped>
  .sidebar {
    width: 250px;
    height: 40vh;
    background-color: #2c3e50;
    color: white;
    padding-top: 20px;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  .sidebar-item {
    padding: 15px;
    text-align: center;
    cursor: pointer;
    border-bottom: 1px solid #34495e;
  }
  
  .sidebar-item:hover {
    background-color: #34495e;
  }
  
  .active {
    background-color: #1abc9c;
  }
  </style>
  