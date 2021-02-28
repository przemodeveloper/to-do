<template>
  <div class="form">
      <input type="text" v-model="title">
      <input type="text" v-model="description">
      <button @click="addTask">Add Task!</button>
  </div>
</template>

<script>
export default {
    props: ['length'],
    data() {
        return {
            title: '',
            description: ''
        }
    },
    methods: {
        addTask() {
            if(this.title != '' && this.description != '') {
                this.$emit('addTask', {id: this.length + 1, title: this.title, description: this.description})
                this.title = '';
                this.description = '';
            }
        }
    }
}
</script>

<style>
    .form {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        border: 1px solid black;
        border-radius: 15px;
        width: 50%;
        margin: 10px auto;
        padding: 10px;
    }

    input {
        margin: 5px;
    }

    button {
        margin: 5px;
    }
</style>