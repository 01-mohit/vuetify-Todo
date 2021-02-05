<template>
  <div class="Todo pa-6">
    <h1 class="  pl-4" >Add your tasks!</h1>
      <v-text-field
      v-model="newTasktitle"
      @click:append="addtask"
      @keyup.enter="addtask"
      class="pa-3"
      outlined
      label="Add task"
      append-icon="mdi-plus"
      hide-details
      clearable
      ></v-text-field>
    <v-list
      flat
      class="pt-0,
      done: false"
    >
    <div v-for="task in tasks" :key="task.id">
        <v-list-item @click="doneTask(task.id)"
        :class="{ 'blue lighten-4'  : task.done}"
        >
          <template v-slot:default >
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title :class="{ 'text-decoration-line-through'  : task.done}"
               >{{task.title}}</v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn
               icon
               @click.stop="deleteTask(task.id)">
                <v-icon color="red">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider
        ></v-divider>
    </div>
    </v-list>
  </div>
  
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Todo',
  data(){
    return{
      newTasktitle: '',
      tasks:[
        // {
        //   id: 1,
        //   title: 'Wake up',
        //   done: false
        // },
        // {
        //   id: 2,
        //   title: 'Get grossary',
        //   done: false
        // },
        // {
        //   id: 3,
        //   title: 'Go to College',
        //   done: false
        // },
        // {
        //   id: 4,
        //   title: 'Complete vuetify project',
        //   done: false
        // },
      ]
    }
  },
  methods:{
    addtask(){
      console.log('addtask')
      let newTask = {
        id: Date.now(),
        title: this.newTasktitle,
        done: false
      }
      this.tasks.push(newTask)
      this.newTasktitle = ''
    },
    doneTask(id){
      // console.log('id: ',id)
      let task = this.tasks.filter(task => task.id === id)[0]
      task.done = !task.done
    },
    deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }

}
</script>
