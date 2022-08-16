
<template>
  <div class="container">
    <Header
    :showAddTaskC="showAddTask"
    @toggle-add="toggleAdd"
    />
    <div v-if="showAddTask">
      <AddText 
    @add-task="addTask"
    /> 
    </div>
    <Tasks
    @toggle-rem = "toggleReminder"
     @delete-task="deleteTask" 
     :tasks='task'/>
  </div>
</template> 
    <script >
        import Header from './components/Header.vue';
        import Tasks from './components/Tasks.vue';
        import AddText from './components/AddText.vue';
        export default{
           name: "App",
           components: {
              Header,
              Tasks,
              AddText
          },
          data(){
            return{
              task: [],
              showAddTask: false
            }
          },
          methods:{
            deleteTask(id){
              this.task = this.task.filter((tas) => tas.id !== id )
            },
            toggleReminder(id){
              this.task = this.task.map((tas) => tas.id === id ? {...tas, reminder: !tas.reminder } : tas
               )
            },
            addTask(newT){
              this.task = [...this.task, newT ]
            },
            toggleAdd(){
              this.showAddTask = !this.showAddTask
            }

          },
          created(){
            this.task = [
              {
                "id": "1",
                "text": "Doctors Appointment",
                "day": "March 5th at 2:30pm",
                "reminder": true
              },
              {
                "id": "2",
                "text": "Meeting with boss",
                "day": "March 6th at 1:30pm",
                "reminder": true
              },
              {
                "id": "3",
                "text": "Food shopping",
                "day": "March 7th at 2:00pm",
                "reminder": false
              }
            ]
          },
          emits: ['delete-task', 'toggle-rem', 'add-task', 'toggle-add']
    
        }
    
    </script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
