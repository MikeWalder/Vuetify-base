<template>
  <div class="todo">

    <v-parallax 
    height="100" 
    src="../../public/hd-wood-background.jpg"
    elevate-on-scroll
    >
      <v-row
      align="center"
      justify="center"
      >
        <v-col
        class="text-center"
        cols="12"
        >
          <div class="text-h3 font-weight-medium"
          >
              To-Do Page
          </div>
        </v-col>
      </v-row>
    </v-parallax>

    <v-text-field
    v-model="newTaskTitle"
    @click:append="addTask"
    @keyup.enter="addTask"
    class="pa-5"
    outlined
    label="Ajouter tâche"
    append-icon="mdi-plus"
    hide-details
    clearable
    >
    </v-text-field>

    <v-list class="pt-0" flat v-for="task in tasks" :key="task.id"> 
      <v-list-item @click="completeTask(task.id)"
      :class="{ 'light-green lighten-2' : task.complete }">

        <template v-slot:default>
          <v-list-item-action>
            <v-checkbox :input-value="task.complete"></v-checkbox>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title :class="{ 'text-decoration-line-through' : task.complete }">{{ task.title }}</v-list-item-title>
          </v-list-item-content>

          <v-list-item-action>
            <v-btn @click.stop="deleteTask(task.id)" icon>
              <v-icon color="red darken-4">mdi-delete</v-icon>
            </v-btn>
          </v-list-item-action>

        </template>
        
      </v-list-item>

      <v-divider></v-divider>
    </v-list>

  </div>
</template>

<script>
  export default {
    data: () => ({
      newTaskTitle: '',
      tasks: [
        {id: 1, title: 'Se lever', complete: false},
        {id: 2, title: 'Coder en Vue 2', complete: false},
        {id: 3, title: 'Faire une nouvelle vidéo sur Youtube', complete: false},
        {id: 4, title: 'Manger le dîner de ce soir', complete: false},
      ]
    }),
    methods: {
      addTask(){
        if(this.newTaskTitle !== ''){
          let newTask = {
            id: Date.now(),
            title: this.newTaskTitle,
            done: false
          }
          this.tasks.push(newTask)
          this.newTaskTitle = ''
        }
      },
      completeTask(id){
        let task = this.tasks.filter(task => task.id === id)[0]
        task.complete = !task.complete
      },
      deleteTask(id){
        this.tasks = this.tasks.filter(task => task.id !== id)
      }
    }
  }
</script>
