<template>
 <div>
    <h1>Math Quiz App</h1>
    <OperatorQuiz v-if="operator" :operator="operator" @goBack="goBack"/>
    <OperatorSelector v-if="!operator" @changeOperator="changeOperator"/>
 </div>
</template>

<script>
import OperatorSelector from './components/OperatorSelector.vue';
import OperatorQuiz from './components/OperatorQuiz.vue';
export default {
  name: 'App',
  data(){
    return {
      operator: null
    }
  },
  components: {
    OperatorSelector,
    OperatorQuiz
  },
  methods : {
    changeOperator(operator)
    {
      this.operator = operator;
    },
    goBack()
    {
      this.operator = null;
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

div {
   display: flex;
  flex-direction: column;
  align-items: center;
}

button {
  box-shadow: 3px 3px rgba(0,0,0,0.15);
  background-color: darkslategray;
  color:white;
  font-size: 36px;
  padding: 5px 20px;
  border: none;
  margin-top:10px;
  margin-bottom: 20px;
  cursor: pointer;
  width: 120%;
}
.answers{
  flex-direction: row !important;
  font-size: 30px;
}
.answers button{
  margin-right: 10px;
}
button:hover {
  border: 2px solid rgba(172, 255, 47, 0.836);
}

@media screen and (max-width: 500px) {
  button {
    width: 100%;
  }
}
</style>
