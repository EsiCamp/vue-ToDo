<template>
  <div id="app">
    <div class="main_wrapper border">
      <Header></Header>
      <AddTask @taskCreated="receiveTitle"></AddTask>
      <ListTasks :tasks="tasks"></ListTasks>
      <button @click="removeCompleted">
        حذف تسک های تکمیل نشده
      </button>
    </div>
  </div>
</template>

<script>

import Header from './components/Header'
import AddTask from './components/AddTask'
import ListTasks from './components/ListTasks'

export default {
  data() {
    return {
      tasks: [
        {
          status: '',
          subject: '',
          id: '',
          isComplete: false
        }
      ]
    }
  },
  components: {
    Header,
    AddTask,
    ListTasks
  },
  methods: {
    receiveTitle(title, id) {
      this.tasks.push({
        subject: title,
        status: 'InComplete',
        id: id,
        isComplete: false
      });
    },
    removeCompleted() {
      this.tasks = this.tasks.filter(task => task.status === 'InComplete');
    }
  }
}
</script>

<style>
  @import "../node_modules/@aasaam/noto-font/dist/font-face.css";
  body {
    direction: rtl;
    margin: 0;
    font-family: "aasaam-Noto", sans-serif;
  }
  button,
  input {
    font-family: "aasaam-Noto", sans-serif;
  }
  .border {
    border: 2px solid #000;
  }
  .main_wrapper {
    max-width: 1200px;
    padding: 0 8px;
    margin: 0 auto;
  }
</style>
