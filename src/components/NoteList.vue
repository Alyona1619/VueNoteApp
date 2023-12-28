<template>
    <div>
      <ul class="list-group">
        <li v-for="note in notes" :key="note.id" class="list-group-item">
          {{ note.text }}
          <span v-if="note.important" class="badge badge-warning ml-2">Important</span>
          <span v-if="note.private" class="badge badge-info ml-2">Private</span>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      notes: Array,
    },
  };
  </script>
  
  <style scoped>
  /* Add custom styles if needed */
  </style>
  