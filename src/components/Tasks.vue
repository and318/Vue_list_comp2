<template>

      <div class="shadow p-3 mb-2 bg-dark text-white rounded col-md-6 d-flex justify-content-between">{{task.task}} <button type="button" class="btn btn-outline-danger btn-sm" @click="remove" ><i class="fas fa-trash-alt"></i></button> </div>
</template>
<script>
export default {
  name: 'Tasks',
  data(){
    return{
listado:""  

  }
},
  props: {
    task: Object,
    index: Number,
       
  },
  methods: {
    remove() {
       this.$emit('removeTask', this.index)
  },
}
}
</script>

<style>

</style>