<template>
  <div id="app">
    <h3>{{ title}}</h3>
    <Tasks :tasks="tasks" v-on:completeTaskEvent="completeTask" v-on:deleteTaskEvent="deleteTask"></Tasks>
    <input @keyup.enter="addNewTask" type="text" class="form-control mb-2" v-model="newTask">
    <button v-on:click="addNewTask" class="btn btn-success btn-block">Add new Task</button>
  </div>
</template>

<script>
import Tasks from "@/components/Tasks.vue";
export default {
  name: "app",
  components: {
    Tasks
  },
  data() {
    return {
      title: " Tasks Apps",
      newTask: null,
      tasks: [
        {
          body: "GO to shop",
          completed: false
        },
        {
          body: "GO to barber",
          completed: false
        },
        {
          body: "GO to school",
          completed: false
        },
        {
          body: "GO to bed",
          completed: false
        }
      ]
    };
  },

  methods: {
    addNewTask() {
      this.tasks.push({
        body: this.newTask,
        completed: false
      });
      this.newTask = null;
    },

    completeTask(task) {
      task.completed = !task.completed;
    },

    deleteTask(index) {
      console.log("delete task " + index);
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  margin-top: 60px;
}

.card {
  padding: 20px;
  background: #eee;
}
</style>
