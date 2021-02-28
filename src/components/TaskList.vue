<template>
  <div class="taskList" v-bind:key="task" v-for="task in tasks">
      <Task :title="task.title" :description="task.description" :id="task.id" @id="sendId" @text="sendChange" @description="sendDescriptionChange"/>
  </div>
</template>

<script>

import Task from './Task';

export default {
    props: ['tasks'],
    components: { Task },
    methods: {
      sendId(id) {
        this.$emit('id', id);
        console.log(id)
      },
      sendChange(text) {
        this.$emit('change', text);
      },
      sendDescriptionChange(description) {
        this.$emit('descriptionChange', description);
      }
    }
}

</script>

<style>

</style>