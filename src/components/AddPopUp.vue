<script setup>

</script>

<template>
  <div class="card">
        <div class="card-body">
          <form action="">
            <div class="row mb-3 align-items-center">
              <div class="input-group">
                <div class="input-group-text">Task</div>
                <input type="text" name="taskname" id="" placeholder="Something" class="form-control">
              </div>
            </div>

            <div class="row mb-3 align-items-center">
              <div class="input-group">
                <div class="input-group-text">Time</div>
                <input type="text" name="duration" id="" placeholder="30" class="form-control">
              </div>
            </div>

            <div class="row align-items-center">
              <div class="col">
                <button type="button" name="" id="" class="btn btn-primary">Submit</button>
              </div>
              <div class="col">
                <button type="button" name="" id="" class="btn btn-primary">Close</button>
              </div>
            </div>
          </form>
        </div>
      </div>
</template>

<style scoped>
  .card {
    width: 25rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>
