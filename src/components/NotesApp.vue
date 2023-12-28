<template>
    <div id="app" class="container">
        <div class="row justify-content-evenly">
            <div class="col-5">
                <div class="card p-5">
                    <h2>Создай заметку</h2>
                    <form>
                        <div class="mb-4">
                            <label for="text" class="form-label text-start">Описание:</label>
                            <input type="text" id="text" v-model="text" class="form-control">
                        </div>
                        <div class="mb-4">
                            <label for="doptext">Дополнительно:</label>
                            <textarea id="doptext" class="form-control" v-model="doptext"></textarea>
                        </div>
                        <div class="mb-4">
                            <label for="type" class="form-label text-start">Область:</label>
                            <select id="type" v-model="type" class="form-select">
                                <option value="Личное">Личное</option>
                                <option value="Работа">Работа</option>
                                <option value="Другое">Другое</option>
                            </select>
                        </div>
                        <label class="form-label">Приоритет:</label>
                        <div class="form-check form-check-inline">
                            <input type="radio" id="high" value="1" v-model="priority" class="form-check-input">
                            <label for="high" class="form-label">1</label>
                        </div>
                        <div class="form-check form-check-inline">
                            <input type="radio" id="medium" value="2" v-model="priority" class="form-check-input">
                            <label for="medium" class="form-label">2</label>
                        </div>
                        <div class="form-check form-check-inline">
                            <input type="radio" id="low" value="3" v-model="priority" class="form-check-input">
                            <label for="low" class="form-label">3</label>
                        </div>

                        <div class="form-check">
                            <input class="form-check-input" type="checkbox" v-model="highlight" id="flexCheckDefault">
                            <label class="form-check-label" for="flexCheckDefault">
                                Выделить заметку цветом
                            </label>
                        </div>

                        <div class="row">
                            <div class="col mb-3">
                                <button v-on:click="add" class="btn btn-success">Добавить</button>
                            </div>
                            <div class="col mb-3">
                                <button v-on:click="reset" class="btn btn-secondary">Сброс</button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>

            <div class="col-6">

                <div class="card p-5">
                    <h2>Список заметок</h2>

                    <ul>
                        <li v-for="note in notes" :key="note.id">
                            <div :class="{ 'border rounded': true, 'bg-warning p-2': note.highlight }">
                                <div class="d-flex justify-content-between align-items-center">
                                    <div class="d-flex align-items-center">
                                        <!-- <span class="mr-2">></span> -->
                                        <div class="text-center">
                                            <p class="m-0">
                                                {{ note.text }}
                                                <br>
                                                Дополнительно: {{ note.doptext }}
                                                <br>
                                                Область: {{ note.type }}
                                                <br>
                                                Приоритет: {{ note.priority }}
                                            </p>
                                        </div>
                                    </div>
                                    <input type="checkbox" v-model="note.done" id="check" class="form-check-input">
                                </div>
                            </div>
                        </li>
                    </ul>



                </div>
            </div>
        </div>
    </div>
</template>

  
<script>
export default {
    data() {
        return {
            text: '',
            doptext: '',
            type: 'Личное',
            priority: '1',
            done: false,
            highlight: false,
            notes: JSON.parse(localStorage.getItem('notes')) || [],
        };
    },

    methods: {
        add() {
            const newNote = {
                id: this.nextNoteId,
                text: this.text,
                doptext: this.doptext,
                type: this.type,
                priority: this.priority,
                done: this.done,
                highlight: this.highlight,
            };

            // if (this.highlight) {
            //     newNote.highlight = true;
            // }

            this.notes.push(newNote);
            this.save();
            this.clean();

        },
        save() {
            localStorage.setItem('notes', JSON.stringify(this.notes));
        },
        clean() {
            this.text = '';
            this.doptext = '';
            this.type = 'Личное';
            this.priority = '1';
            this.done = false;
            this.highlight = false;
        },
        reset() {
            localStorage.removeItem('notes');
            this.notes = [];
        },
    },
};
</script>
  
<style>
ul {
    list-style: none;
}

div {
    margin: 10px;
}

button {
    margin: 20px;
}
</style>