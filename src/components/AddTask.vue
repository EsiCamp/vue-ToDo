<template>
  <div>
    <form class="main_form">
      <input type="text" placeholder="افزودن تسک" v-model="taskTitle">
      <button @click.prevent="addTask">
        افزودن تسک
      </button>
      <p>
        {{ errors }}
      </p>
    </form> 
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  data() {
    return {
      taskTitle: '',
      errors: ''
    };
  },
  methods: {
    addTask() {
      if (this.taskTitle == '') {
        this.errors = "تسک خود را وارد نمایید"
      } else {
        this.errors = '';
        this.$emit('taskCreated', this.taskTitle, uuidv4());
        this.taskTitle = '';
      }
    }
  }
}
</script>

<style>
  .main_form {
    text-align: center;
  }
</style>
