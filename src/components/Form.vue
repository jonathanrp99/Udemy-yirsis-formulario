<template>
    <form @submit.prevent>
    <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Projects</label>
    <input type="text" class="form-control" 
    required
     id="exampleInputEmail1" 
     aria-describedby="emailHelp">
    </div>
    <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Tasks</label>
    <select class="form-select" 
    required>
        <option disabled selected value="">Pick one...</option>
        <option value="1">Web App with Vue.js</option>
        <option value="2">Backend service using node</option>
        <option value="3">React native movile App</option>
    </select>
    </div>
    <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Priority</label>
    <input type="checkbox" class="form-check-input" />
    </div>
    <button @click="registerProject" type="submit" class="btn btn-primary">Save</button>
    </form>
</template>

<script setup>
    function registerProject () {
        console.log("pinga registrada")
    }
</script>