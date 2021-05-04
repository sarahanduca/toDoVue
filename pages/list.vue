<template>
  <div align="center" class="d-block mt-5">
    <h1>My todo List 📝</h1>
    <b-container fluid class="justify-content-md-center w-50">
      <b-row>
        <b-col>
          <div class="inputs">
            <b-input
              placeholder="Todo"
              v-on:keyup.enter="addTask(task)"
              v-model="task"
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
              v-for="task in tasks"
              :key="task.id"
            >
              <b-form-checkbox
                :id="task.id"
                :name="task.id"
                value="done"
                unchecked-value="not_done"
                :class="{ done: status == 'done' }"
              >
                {{ task.task }}
                <!-- 
            <b-button size="sm" class="mx-3" variant="outline-danger"
              >Remove</b-button
            >
            <b-button size="sm" variant="outline-info">Edit</b-button> -->
              </b-form-checkbox>
            </div>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tasks: [{ id: 1, task: 'passear com o doguinho' }],
    }
  },
  methods: {
    addTask(task) {
      if (task != '') {
        this.tasks.push({
          id: this.tasks.length + 1,
          task,
        })
        this.task = ''
      }
    },
    removeAllTask() {
      this.tasks = []
    },
  },
}
</script>
<style>
* {
  background: rgb(233, 225, 178);
}
</style>
