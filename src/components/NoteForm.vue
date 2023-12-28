<template>
    <div>
      <form @submit.prevent="addNote">
        <div class="form-group">
          <label for="text">Note:</label>
          <input type="text" id="text" v-model="text" class="form-control">
        </div>
        <div class="form-check">
          <input v-model="isImportant" class="form-check-input" type="checkbox" id="isImportant">
          <label class="form-check-label" for="isImportant">Important</label>
        </div>
        <div class="form-check">
          <input v-model="isPrivate" class="form-check-input" type="checkbox" id="isPrivate">
          <label class="form-check-label" for="isPrivate">Private</label>
        </div>
        <button type="submit" class="btn btn-primary">Add Note</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        noteText: '',
        isImportant: false,
        isPrivate: false,
      };
    },
    methods: {
      addNote() {
        // Implement logic to add a new note
        this.$emit('add-note', {
          text: this.noteText,
          important: this.isImportant,
          private: this.isPrivate,
        });
  
        // Clear the form
        this.noteText = '';
        this.isImportant = false;
        this.isPrivate = false;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add custom styles if needed */
  </style>
  