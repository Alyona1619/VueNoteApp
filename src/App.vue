<!-- <template>
  <div id="app" class="container mt-5">
    <div class="row">
      <div class="col-md-6 border rounded">
        <h3>Create note</h3>
        <note-form @add-note="addNote"></note-form>
      </div>
      <div class="col-md-6">
        <h3>Notes</h3>
        <note-list :notes="notes"></note-list>
      </div>
    </div>
  </div>
</template>

<script>
import NoteForm from './components/NoteForm.vue';
import NoteList from './components/NoteList.vue';

export default {
  components: {
    NoteForm,
    NoteList,
  },
  data() {
    return {
      notes: [],
    };
  },
  methods: {
    addNote(newNote) {
      // Generate a unique ID for the note
      newNote.id = Date.now();

      // Add the note to the list
      this.notes.push(newNote);
    },
  },
};
</script>

<style>
h1 {
  margin-bottom: 100px; /* Добавьте нужное значение отступа в пикселях */
}
</style> -->







<template>

  <header>
  </header>

  <main>
    <NotesApp />
  </main>

</template>

<script setup>
import NotesApp from './components/NotesApp.vue'
</script>





 <!-- <template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>  -->