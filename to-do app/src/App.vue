<template>
  <div class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
      <div class="mb-4">
        <h1 class="text-grey-darkest">Todo List</h1>
        <div class="flex mt-4">
          <input
            v-model="task"
            class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker"
            placeholder="Add Todo"
          />
          <button
            @click="addTask"
            class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal"
          >
            Add
          </button>
        </div>
      </div>
      <div>
        <div
          v-for="(task, index) in tasks"
          :key="index"
          class="flex mb-4 items-center"
        >
          <p
            class="w-full"
            :class="{ 'line-through text-green': task.completed }"
          >
            {{ task.text }}
          </p>
          <button
            @click="toggleTask(index)"
            class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green border-green hover:bg-green"
          >
            <span v-if="task.completed">Undo</span>
            <span v-else>Done</span>
          </button>
          <button
            @click="removeTask(index)"
            class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red"
          >
            Remove
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: '', // Holds the input value
      tasks: [] // List of tasks
    };
  },
  methods: {
    addTask() {
      // Add a new task to the list
      if (this.task.trim() !== '') {
        this.tasks.push({ text: this.task, completed: false }); // Add task with completion status
        this.task = ''; // Clear input field
      }
    },
    toggleTask(index) {
      // Toggle task completion
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    removeTask(index) {
      // Remove task from the list
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped>
/* Scoped styles for the component */
</style>
