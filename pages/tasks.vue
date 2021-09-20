<template>
  <div>
    <navbar />
    <!-- //sudGHVNK;ALsHFNVilsdkhgnvlisdka.hgvbj;kSDLAK.;FHVBKDSJ,ZKHVNBSDJKZBFV DSHKAMB-->
    <!-- {{message}}
    <div>
      <input type="text" v-model="newMessage">
      <button @click="changeYo()">change</button>
    </div> -->
    <!-- //sudGHVNK;ALsHFNVilsdkhgnvlisdka.hgvbj;kSDLAK.;FHVBKDSJ,ZKHVNBSDJKZBFV DSHKAMB-->
    <h1>Hello</h1>
    <h3>You can manage your tasks here</h3>
    <section>
      <div class="head">
        <button class="title" @click="SaveAll()">Save All</button>
        <button @click="addTask()">Add Task</button>
      </div>
      <ul class="tasks">
        <li :key="task.id"  class="single-task" v-for="task in tasks" >
          <svg height="32px" viewBox="0 -11 512.02797 512" width="32px" xmlns="http://www.w3.org/2000/svg" v-show="task.isCompeleted"  class="svg">
            <path d="m441.644531 247.59375-11.457031-32.554688-123.582031 123.585938c-12.074219 12.097656-28.160157 18.75-45.25 18.75-17.085938 0-33.171875-6.652344-45.246094-18.75l-90.667969-90.667969c-12.097656-12.074219-18.753906-28.160156-18.753906-45.246093 0-17.089844 6.65625-33.175782 18.753906-45.25 12.074219-12.09375 28.160156-18.75 45.246094-18.75 17.089844 0 33.175781 6.65625 45.25 18.75l45.417969 45.398437 121.6875-121.683594-8.195313-23.253906-3.773437-22.570313c-2.367188-14.464843-11.90625-26.453124-25.453125-32.066406-13.609375-5.652344-28.796875-3.902344-40.722656 4.652344l-59.285157 42.921875-59.949219-43.03125c-12.03125-8.488281-27.261718-10.175781-40.789062-4.5-13.4375 5.632813-22.890625 17.601563-25.257812 31.980469l-11.605469 72.253906-72.683594 12.074219c-14.441406 2.371093-26.429687 11.90625-32.0625 25.453125-5.632813 13.589844-3.882813 28.820312 4.671875 40.746094l42.902344 59.285156-43.03125 59.945312c-8.46875 12.03125-10.175782 27.285156-4.5 40.789063 5.652344 13.441406 17.597656 22.890625 31.976562 25.261719l72.257813 11.625 12.074219 72.660156c2.347656 14.421875 11.820312 26.390625 25.257812 32.023437 13.546875 5.671875 28.800781 3.988281 40.941406-4.609375l59.285156-42.921875 59.796876 42.921875c7.316406 5.226563 15.828124 7.914063 24.46875 7.914063 5.480468 0 10.984374-1.066407 16.253906-3.261719 13.570312-5.632812 23.085937-17.621094 25.453125-32.023438l11.625-72.253906 72.660156-12.074218c14.421875-2.371094 26.371094-11.820313 32.023437-25.261719 5.675782-13.503907 3.988282-28.757813-4.609374-40.9375zm0 0" fill="#f57a07"/>
            <path d="m261.355469 314.710938c-5.460938 0-10.921875-2.089844-15.082031-6.25l-90.667969-90.667969c-8.339844-8.339844-8.339844-21.824219 0-30.164063 8.34375-8.34375 21.824219-8.34375 30.167969 0l75.582031 75.582032 214.25-214.25c8.34375-8.339844 21.824219-8.339844 30.167969 0 8.339843 8.339843 8.339843 21.824218 0 30.164062l-229.335938 229.335938c-4.160156 4.160156-9.621094 6.25-15.082031 6.25zm0 0" fill="#607d8b"/>
          </svg>
          <h4 class="task-title">{{ task.title }}</h4>
          <p class="describe-task" @dblclick="compeleted(task)">{{ task.description }}</p>
          <button  class="edit-task" @click="EditTask(task.id)">Edit Task</button>
          <button  class="delete-task" @click="DeleteTask(task.id)">Delete Task</button>
        </li>
      </ul>
      <addingtask class="addTaskForm"  @callmyfunc="closeAddTask" :showAddTask="showAddTask"  :needEdit="needEdit" @savetask="SaveTask" :userdescribe="userDescribe" :usertitle="userTitle" :mustdelete="mustdelete" />
    </section>
  </div>
</template>
<script>
import navbar from "../components/navbar.vue";
import addingtask from "../components/addingtask.vue";
export default {
  data() {
    return {
      userobject:'',
      userTitle:'',
      userDescribe:'',
      showAddTask: false,
      message: '',
      newMessage: '',
      needEdit: false,
      mustdelete:'',
      tasks:[
          //{title: 'play tryndamere', description: 'we have 4 games left in plat promo so play them and free my mind from that you bag of garbage you must win that shiiiiiiiiiiiiiiit', id:'1', isCompeleted : false},
      ]
    };
  },
  //sudGHVNK;ALsHFNVilsdkhgnvlisdka.hgvbj;kSDLAK.;FHVBKDSJ,ZKHVNBSDJKZBFV DSHKAMB
  mounted(){
    //const storedArrey = localStorage.getItem("tasks")
    //this.message =storedArrey
    const storedArrey = localStorage.getItem("tasks")
    this.tasks = JSON.parse(storedArrey)
  },
  //sudGHVNK;ALsHFNVilsdkhgnvlisdka.hgvbj;kSDLAK.;FHVBKDSJ,ZKHVNBSDJKZBFV DSHKAMB
  components: {
    navbar,
    addingtask,
  },
  methods: {
    closeAddTask() {
      if(this.needEdit){
        this.needEdit = false
      }
      this.showAddTask = false;
    },
    SaveTask(a, b, c){ 
      this.tasks.push({title:a,description:b, id:(Math.random()) * 10000, isCompeleted:false})
      this.DeleteTask(c)
      this.showAddTask = false
      this.needEdit = false
      
    },
    SaveAll(){
      localStorage.setItem("tasks", JSON.stringify(this.tasks))
    },
    addTask() {
      this.showAddTask = true;
    },
    compeleted(task){
      task.isCompeleted = !task.isCompeleted
    },
    DeleteTask(num){
      this.tasks = this.tasks.filter((task)=>num !== task.id)
    },
    EditTask(id){
      this.showAddTask = true
      this.needEdit = true
      this.userobject = this.tasks.filter((task)=>id === task.id)
      this.userTitle = this.userobject[0].title
      this.userDescribe = this.userobject[0].description
      this.mustdelete = id
      console.log(this.mustdelete)
    },
    //FASKHGJDSOGJNisodlkghvbkasjkhvnb;uDKSJLHFNVKUJSDHNVUSKDAJBVDSkj
    // changeYo(){
    //   localStorage.setItem('tasks', this.newMessage);
    //   this.message = this.newMessage;
    //   this.newMessage = '';
    // },
    //gbvasnk.vnzsjklbkasbgnksGNlbkaSNg;liKVJShdngJLVhsdbilgjvhSNDlV
  },
};
</script>
<style scoped>
.svg{
    padding-top: 15px;
    padding-left: 10px;
}
.addTaskForm{
    width: 100%;
    height: 40%;
    background-color: rgb(70, 66, 66);
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.addTaskForm:active{
    opacity: 0.1;
}
ul {
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  border-top: 3px solid #f57a07;
  border-bottom: 3px solid #f57a07;
}
button {
  width: 100px;
  height: 50px;
  margin-top: 10px;
  margin-block: 10px;
  border: 1.5px solid #977a5f;
  border-radius: 5px;
  background-color: #e99445;
  color: #7a7979;
  cursor: pointer;
}
button:active {
  transform: scale(90%);
}
h2 {
  color: rgb(7, 62, 110);
}
div {
  width: 100vw;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
}
h1 {
  width: 100%;
  margin-top: 0;
}
h3 {
  width: 100%;
}
h4{
    padding-left: 5px;
      color: black
}
section {
  background-color: rgb(177, 176, 176);
  border: 3px solid #f57a07;
  border-radius: 3px;
  width: 70%;
  height: 70vh;
}
.head {
  width: 100%;
  display: flex;
  justify-content: space-around;
}
</style>


