<template>
  <div id="app">
    <h1>Tasks</h1>

    <NewTask @taskAdd="addTast($event)" :msg="msg"></NewTask>
    <TaskGrid :tasks="tasks" />
  </div>
</template>

<script>
import NewTask from "./components/NewTask";
import TaskGrid from "./components/TaskGrid.vue";

export default {
  components: { TaskGrid, NewTask },
  data() {
    return {
      tasks: [
        { name: "Fazer as compras", pending: false },
        { name: "Pagar as contas", pending: true }
      ],
      msg: {
        text: "",
        typeMessage: ""
      }
    };
  },
  methods: {
    addTast(event) {

	 if(event.name){
			const sameName = task =>
			task.name.toUpperCase() === event.name.toUpperCase();
			const reallyNew = this.tasks.filter(sameName).length == 0;
		if (reallyNew) {
			this.tasks.push(event);
			this.createMessage(3000, "Task add with success", "success");
		} else {
			this.createMessage(3000, "this task exist", "warning");
		}
	 }else {
		 this.createMessage(2000,'Please, insert a new task', 'error')
	 }	     
    },

    createMessage(time, text, type) {
      this.msg.text = text;
      this.msg.typeMessage = type;
      setTimeout(() => {
        this.msg.text = "";
        this.msg.typeMessage = "";
      }, time);
    }
  }
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
