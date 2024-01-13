<script setup>
  import {ref} from 'vue';

  const tasks = ref([]);

  const taskGiven = ref("");
  const timeGiven = ref(0);

  function addTask() {
    if (taskGiven.value !== '' && timeGiven.value > 0) {
      tasks.value.push({ id: tasks.value.length, name: taskGiven.value, time: timeGiven.value, });
      taskGiven.value = "";
      timeGiven.value = 0;
    } else {
      alert("Please enter value!")
    }
  }

  function removeTask(num) {
    tasks.value.splice(num, 1);
  }

  const hide = ref(true);

  function hidePopUp() {
    hide.value = true;
    taskGiven.value = "";
    timeGiven.value = 0;
  }

  function showPopUp() {
    hide.value = false;
  }
 
</script>

<template>
  <div class="container">

    <div>
      <h1>Welcome to Task Manager</h1>
    </div>
    <hr/>
    
    <div class="row">

      <div class="col">
        <h2>Add Task</h2>
        <hr/>
        <button @click="showPopUp()" type="button" class="btn btn-primary">Add Task</button>
      </div>

      <!-- Show Task list  -->
      <div class="col">
        <h2>To Do</h2>
        <hr/>

        <!-- Render To-Do-List from Tasks-->
        <ul v-for="(task, index) in tasks" :key="index" class="list-group">
          <li class="list-group-item d-flex justify-content-between align-items-center mb-1">
            <strong>{{ index + 1 }})</strong> {{ task.name }} - {{ task.time }} minutes
            <span @click="removeTask(index)" class="btn bg-primary rounded-pill" style="cursor: pointer;">X</span>
          </li>
        </ul>
      </div>

    </div>

    <!-- Pop Up Window to take user input -->
    <div class="card" :style="hide? 'display: none': ''">
      <div class="card-body">
        <form @submit.prevent action="">
          <div class="row mb-3 align-items-center">
            <div class="input-group">
              <div class="input-group-text"><strong>Task Name</strong></div>
              <input v-model="taskGiven" type="text" name="taskname" id="" placeholder="Review practice code" class="form-control" required>
            </div>
          </div>

          <div class="row mb-5 align-items-center">
            <div class="input-group">
              <div class="input-group-text"><strong>Time</strong></div>
              <input v-model.num="timeGiven" type="number" name="duration" id="" placeholder="30" class="form-control" required>
            </div>
          </div>

          <div class="row align-items-center">
            <div class="col">
              <button @click="addTask(); hidePopUp()" type="button" name="" id="" class="btn btn-primary">Submit</button>
            </div>
            <div class="col">
              <button @click="hidePopUp()" type="button" name="" id="" class="btn btn-primary">Close</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .card {
    background-color: aquamarine;
    width: 30rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>
