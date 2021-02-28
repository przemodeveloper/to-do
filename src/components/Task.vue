<template>
  <div class="task">
      <h1 v-if="isEdited" @click="switchToEdit">{{ title }}</h1>
      <div v-else>
          <input type="text" v-model="editedTitle"/>
          <button @click="saveEdited">Save</button>
      </div>
      <p v-if="isDescriptionEdited" @click="switchToEditDescription">{{ description }}</p>
      <div v-else>
          <input type="text" v-model="editedDescription"/>
          <button @click="saveEditedDescription">Save</button>
      </div>
      <button @click="passId">Delete</button>
  </div>
</template>

<script>
export default {
    props: ['title', 'description', 'id'],
    data() {
        return {
            isEdited: true,
            editedTitle: '',
            isDescriptionEdited: true,
            editedDescription: ''
        }
    },
    methods: {
        passId() {
            this.$emit('id', this.id);
        },
        switchToEdit() {
            this.isEdited = false;
        },
        saveEdited() {
            if(this.editedTitle != '') {
                this.$emit('text', {id: this.id, newText: this.editedTitle});
                this.isEdited = true;
            }
        },
        switchToEditDescription() {
            this.isDescriptionEdited = false;
        },
        saveEditedDescription() {
            if(this.editedDescription != '') {
                this.$emit('description', {id: this.id, newTextDescription: this.editedDescription});
                this.isDescriptionEdited = true;
            }
        }
    }
}
</script>

<style>
    h1, p {
        cursor: pointer;
    }

    .task {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        border: 1px solid black;
        border-radius: 15px;
        width: 50%;
        margin: 10px auto;
    }
</style>