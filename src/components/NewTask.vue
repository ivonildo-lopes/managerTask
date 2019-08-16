<template>
  <div class="new-task">
    <input class="form-element" type="text" @keydown.enter="add" v-model="name" />
    <button class="form-element" @click="add">+</button>
    <p :class="stateClass">{{msg.text}}</p>
  </div>
</template>
    
<script>
export default {
  data() {
    return {
      name: ""
    };
  },
  props: {
    msg: {
      text: "",
      typeMessage: ""
    }
  },
  methods: {
    add() {
      this.$emit("taskAdd", { name: this.name, pending: true });
      this.name = "";
    }
  },
  computed: {
    stateClass() {
      return {
        error: this.msg.typeMessage == "error",
        info: this.msg.typeMessage == "info",
        success: this.msg.typeMessage == "success",
        warning: this.msg.typeMessage == "warning"
      };
    }
  }
};
</script>
<style >

.form-element {
    outline: none;
    font-size: 2rem;
    border: 1px solid #FFF;
    padding: 5px 10px 8px;
    color: #FFF
}

input.form-element {
    width: 500px;
    background: #FFF2;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
}

button.form-element {
    border-left: none;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    background-color: #2196F3;

}

/* css das mensagens */
.error {
  box-sizing: border-box;
  height:50px;  
  border-radius: 8px;
  color: #DDD;
  background-color: #F44336;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  display: flex;
}
.success {
  box-sizing: border-box;
  height:50px;  
  border-radius: 8px;
  color: #DDD;
  border-left: 12px solid #0A8F08;
  background-color: #4CAF50;
   justify-content: center;
   align-items: center;
  flex-wrap: wrap;
  display: flex;
}

.info { 
  box-sizing: border-box;
  height:50px;
  border-radius: 8px;
  color: #DDD;
  border-left: 12px solid rgb(85, 127, 218);
  background-color: rgba(33, 130, 160, 0.808);
   justify-content: center;
   align-items: center;
  flex-wrap: wrap;
  display: flex;
}

.warning {
  box-sizing: border-box;
  height:50px;
  border-radius: 8px;  
  color: rgb(20, 4, 77);
  border-left: 12px solid rgb(214, 226, 43);
  background-color: rgb(241, 240, 138);
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  display: flex;
}
</style>