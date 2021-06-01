<template>
  <div align="center" class="d-block mt-5">
    <h1>My todo List 📝</h1>
    <b-container fluid class="justify-content-md-center w-50">
      <b-row>
        <b-col>
          <div>
            <b-input
              ref="input"
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
              <b-button
                variant="outline-danger"
                class="mt-3"
                v-on:click="removeDoneTasks()"
                >Remove Done Tasks</b-button
              >
            </div>
          </div>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="tarefas px-5">
          <div class="mt-5" align="left">
            <div
              id="list"
              class="mt-2"
              v-for="task in listaTarefa"
              :key="task.id"
            >
              <b-form-checkbox
                :id="task.id"
                v-model="task.status"
                value="done"
                unchecked-value="not_done"
                :class="{ done: task.status == 'done' }"
                class="mt-2"
              >
                {{ task.tarefa }}

                <b-input
                  :class="{ editTask: task.clicked == 'off' }"
                  v-on:keyup.enter="task.clicked = 'off'"
                  ref="input"
                  v-model="task.tarefa"
                  :value="task.tarefa"
                />
                <br />
                <div class="crudbtn">
                  <b-button
                    size="sm"
                    class="mx-3"
                    v-on:click="deleteItem(task)"
                    variant="outline-danger"
                    >Remove</b-button
                  >
                  <b-button
                    size="sm"
                    variant="outline-info"
                    v-on:click="task.clicked = 'on'"
                    >Edit</b-button
                  >
                </div>
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
      idCount: 0,
      task: '',
      listaTarefa: [
        {
          id: this.idCount,
          tarefa: 'passear com o doguinho',
          status: 'not_done',
          clicked: 'off',
        },
      ],
    }
  },
  methods: {
    addTask(task) {
      if (task != '' && task != ' ') {
        this.idCount += 1
        this.listaTarefa.push({
          id: this.idCount.toString(),
          tarefa: this.task,
          status: 'not_done',
          clicked: 'off',
        })
      }
      this.task = ''
    },
    removeAllTask() {
      this.listaTarefa = []
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
.done label {
  font-style: italic;
  text-decoration: line-through;
}

label {
  cursor: pointer;
  margin: 2rem 0;
}

label:hover .crudbtn {
  display: block;
}

.editTask {
  display: none;
}

.crudbtn {
  display: none;
}
</style>
