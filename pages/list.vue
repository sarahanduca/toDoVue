<template>
  <div align="center" class="d-block mt-5">
    <h1>My todo List 📝</h1>
    <b-container fluid class="justify-content-md-center w-50">
      <b-row>
        <b-col>
          <div class="inputs">
            <b-input
              placeholder="Todo"
              v-model="task"
              v-on:keyup.enter="addTask(task)"
            />
            <div class="buttons">
              <b-button
                variant="outline-dark"
                class="mt-3"
                v-on:click="addTask(task)"
                >Add Task</b-button
              >
              <b-button
                variant="outline-danger"
                class="mt-3"
                v-on:click="removeAllTask()"
                >Remove All</b-button
              >
            </div>
          </div>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <div class="mt-5 w-50" align="left">
            <div
              id="list"
              ref="list"
              class="mt-2"
              v-for="task in listaTarefa"
              :key="task.id"
            >
              <b-form-checkbox
                ref="input"
                :id="task.id"
                :name="task.id"
                v-model="task.status"
                value="done"
                unchecked-value="not_done"
                :class="{ done: task.status == 'done' }"
                class="mt-2"
              >
                {{ task.tarefa }}
                <br />
                <b-button
                  size="sm"
                  class="mx-3"
                  v-on:click="deleteItem(task)"
                  :class="{ crudbtn: task.status == 'not_done' }"
                  variant="outline-danger"
                  >Remove</b-button
                >
                <b-button
                  size="sm"
                  :class="{ crudbtn: task.status == 'not_done' }"
                  variant="outline-info"
                  >Edit</b-button
                >
              </b-form-checkbox>
            </div>
          </div>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <b-button variant="dark" class="mt-5">
            <NuxtLink to="/" class="nuxtlink">Home</NuxtLink>
          </b-button>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listaTarefa: [
        { id: 1, tarefa: 'passear com o doguinho', status: 'not_done' },
      ],
    }
  },
  methods: {
    addTask(task) {
      if (task != '' && task != ' ') {
        this.listaTarefa.push({
          id: this.listaTarefa.length + 1,
          tarefa: this.task,
          status: 'not_done',
        })
      }
      this.task = ''
    },
    removeAllTask() {
      this.listaTarefa = []
    },
    removeChecked() {
      this.listaTarefa.forEach((e) => {
        e.status == 'done'
      })
    },
    deleteItem(task) {
      const index = this.listaTarefa.indexOf(task)
      this.listaTarefa.splice(index, 1)
    },
  },
}
</script>
<style>
* {
  background: rgb(233, 225, 178);
}
.done {
  font-style: italic;
}
.crudbtn {
  display: none;
}
</style>
