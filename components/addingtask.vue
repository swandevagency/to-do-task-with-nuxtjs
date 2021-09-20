<template>
  <div v-if="showAddTask">
      <input type="text" placeholder="task title" maxlength="25" v-model="taskTitle" v-if="!needEdit">
      <input type="text"  maxlength="25"  v-if="needEdit"   v-model="usertitle">
      <textarea placeholder="describe your task" cols="30" rows="3" v-model="taskDescribe" v-if="!needEdit"></textarea>
      <textarea v-if="needEdit" cols="30" rows="3" v-model="userdescribe"></textarea>
      <button class="btn" @click="closeAddingTask()">Close</button>
      <button class="btn" v-if="!needEdit" @click="saveTask()">Save Task</button>
      <button class="btn" v-if="needEdit" @click="saveChanges()">Save Changes</button>
      </div>
</template>

<script>
export default {
    props:[
      "showAddTask",
      "needEdit",
      "usertitle",
      "userdescribe",
      "mustdelete"
    ],
    data(){
      return{
        taskTitle:'',
        taskDescribe:'',
      }
    },
    //mounted(){
    //   setTimeout(() => {
    //       this.taskTitle = this.usertitle
    //   }, 1000);
    // },
  methods:{
      closeAddingTask(){
          this.$emit('callmyfunc');
          if(this.needEdit){
            this.taskTitle = ''
            this.taskDescribe= ''
          }
      },
      saveTask(){
        this.$emit('savetask', this.taskTitle, this.taskDescribe, this.mustdelete);
        this.taskTitle = ''
        this.taskDescribe = ''
      },
      saveChanges(){
        this.taskTitle = this.usertitle,
        this.taskDescribe = this.userdescribe
        this.saveTask()
      }
  }
};
</script>
<style>
.btn{
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
textarea{
  width: 95%;
}
</style>