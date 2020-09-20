<template>
<div id="app">
    <div class="container mt-5">
        <div class="flex-row mt-5 mb-5">
            <h3 class="text-center">{{message}}</h3>
        </div>
        <div class="flex-row">
            <div class="d-flex justify-content-center ">
                <div class="input-group mb-3 col-md-4">
                    <input v-model="newTask" @keyup.enter="addTask" type="text" class="form-control" placeholder="Ingrese nueva tarea">
                    <div class="input-group-append">
                        <button @click="addTask" class="btn btn-outline-secondary" type="button">Agregar</button>
                    </div>
                </div>
            </div>
        </div>
        <div class="flex-row">
            <div class="col-md-12">
                <h4 class="text-center my-5">Mis tareas</h4>
            </div>
            <div class="d-flex  flex-column col-md-12 align-items-center">
                <Tasks v-for="(task, index) in tasks" v-bind:task="task" v-bind:index="index" v-bind:key="index" v-on:removeTask="remove">
                </Tasks>
            </div>
        </div>

    </div>

</div>
</template>

<script>
import Tasks from './components/Tasks.vue'
export default {
    name: 'App',
    components: {
        Tasks
    },
    data() {
        return {
            tasks: [],
            newTask: "",
            message: "Mi lista de tareas "
        }
    },
    methods: {

        remove(index) {
            this.tasks.splice(index, 1);
            console.log(index);

        },
        addTask() {
            if (this.newTask === "" || this.newTask.length < 3) {
                alert('Vamos, hay tareas de más de 4 letras!')
            } else {
                this.tasks.push({
                    task: this.newTask,
                });
                this.newTask = "";
            }
        },
    },
}
</script>

<style>

</style>
