<template>
    <div class="row">
        <div class="col-12 mb-4">
            <h3 class="text-center">Progress: {{percentage}}%</h3>
            <div class="progress">
                <div class="progress-bar progress-bar-striped progress-bar-animated bg-success"
                role="progressbar"
                aria-valuenow="percentage"
                aria-valuemin="0"
                aria-valuemax="100"
                :style="`width: ${percentage}%`"
                >
            </div>
            </div>
        </div>
        <div class="col-12 col-md-4">
            <form @submit.prevent>
        <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Project</label>
        <input  v-model="project" class="form-control" 
        required
        id="exampleInputEmail1" 
        aria-describedby="emailHelp">
        </div>
        <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Tasks</label>
        <select v-model="type" class="form-select" 
        required>
            <option disabled selected value="">Pick one...</option>
            <option>Web App with Vue.js</option>
            <option>Backend service using node</option>
            <option>React native movile App</option>
        </select>
        </div>
        <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">Priority</label>
        <input v-model="priority" type="checkbox" class="form-check-input" />
        </div>
        <button @click="registerProject" type="submit" class="btn btn-primary">Save</button>
        </form>
    </div>
        <div class="col-12 col-md-8">
            <h3>
        Projects count: {{ count }}
    </h3>
    <div class="table-responsive">
        <table class="table table-dark">
            <thead>
                <tr>
                    <th>#</th>
                    <th>project</th>
                    <th>type</th>
                    <th>priority</th>
                    <th>completed</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(project, index) in projects" :key="index">
                    <td>{{index +1 }}</td>
                    <td>{{project.project}}</td>
                    <td>{{project.type}}</td>
                    <td @click="changeState(project, 'priority')"
                     :class="project.priority ? 'bg-success' : 'bg-danger'">
                     {{project.priority ? "Yes" : "No"}}
                    </td>
                    <td @click="changeState(project, 'completed')"
                     :class="project.completed ? 'bg-success' : 'bg-danger'">
                     {{project.completed ? "Completed" : "Incompleted"}}
                    </td>
                </tr>
            </tbody>
        </table>
       </div>
    </div>
</div>
</template>

<script setup>
import { ref } from '@vue/reactivity';
import { computed } from '@vue/runtime-core';


const project = ref("")
const type = ref("")
const priority = ref(false)
const projects = ref([])
const completed = ref(false)

function registerProject () {
    const thisProject = {
    project: project.value,
    type: type.value,
    priority: priority.value
    }
    projects.value.push(thisProject)

    
    project.value = ""
    type.value = ""
    priority.value = false
}
function changeState (project, field) {
    project[field] = !project[field]
}

const count = computed(() => {
    return projects.value.length
})

const percentage = computed(() => {
    const completedProgress = ref(0)
    projects.value.map(project => {
        if(project.completed)
        completedProgress.value++
    })
    
    return (completedProgress.value * 100) / count.value || 0
}) 


    
</script>