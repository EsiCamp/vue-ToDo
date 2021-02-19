<template>
  <div>
    <div v-for="(task, index) in tasks" :key="task + index">
      <div v-if="task.subject != '' || task.status != ''">
        <button @click="changeStatus(task.id)" :class="{completed: task.isComplete}">
          {{ task.subject }}
          {{ task.status }}
        </button>
        <button @click="removeTask(task.id)">
          x
        </button>
      </div>
    </div>
    <p>
      تعداد تسک های کامل نشده:
      {{ taskCounter }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  props: {
    tasks: Array
  },
  methods: {
    changeStatus(id) {
      console.log(id);
      const result = this.tasks.find(task => task.id === id);
      result.status = "Completed";
      result.isComplete = !result.isComplete;
    },
    removeTask(id) {
      this.tasks.splice(id, 1);
    },
  },
  computed: {
    taskCounter() {
      const counter = this.tasks.filter(task => task.status === 'InComplete'); 
      return counter.length;
    }
  }
}
</script>

<style>
  .completed {
    text-decoration: line-through;
    background-color: #008000;
    color: #fff;
    border-radius: 7px;
    padding: 4px 25px;
  }
</style>
