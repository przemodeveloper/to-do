<template>
  <div>
    <TaskList :tasks="tasks" @id="deleteTask" @change="acceptChange" @descriptionChange="acceptChangeDescription"/>
    <Form :length="tasks.length" @addTask="addNewTask" />
  </div>
</template>

<script>

import TaskList from './components/TaskList';
import Form from './components/Form';

export default {
  name: 'App',
  components: { TaskList, Form },
      data() {
        return {
            tasks: [
                {
                    id: 1,
                    title: 'Hello World',
                    description: 'this is the world'
                },
                {
                    id: 2,
                    title: 'Hello Mars',
                    description: 'this is the mars'
                },
                {
                    id: 3,
                    title: 'Hello Jupiter',
                    description: 'this is the jupiter'
                }
            ]
        }
    },
    methods: {
      addNewTask(taskObject) {
        const listOfTasks = this.tasks.concat(taskObject);
        this.tasks = listOfTasks;
      },
      deleteTask(id) {
        const filteredList = this.tasks.filter(element => {
          return element.id != id;
        })
        this.tasks = filteredList;
      },
      acceptChange(text) {
        const fnd = this.tasks.find(element => {
          return element.id === text.id;
        })
        fnd.title = text.newText;
        console.log(this.tasks);
      },
      acceptChangeDescription(description) {
        const fnd = this.tasks.find(element => {
          return element.id === description.id;
        })
        fnd.description = description.newTextDescription;
      }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
