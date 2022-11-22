<template>
  <div id="app">
    <h1>Kuis Matematika</h1>
    <OperatorQuizVue v-if="operator" @onBack="clearOperator" :operator="operator"/>
    <OperatorSelect v-if="!operator" @select="onSelect"/>
  </div>
</template>

<script>
import OperatorSelect from "./components/OperatorSelect.vue"
import OperatorQuizVue from "./components/OperatorQuiz.vue"
export default {
  name: 'App',
  components:{OperatorSelect, OperatorQuizVue},
  data(){
    return{
      operator: null
    }
  },
  methods:{
    onSelect(operator){
      this.operator = operator
    },
    clearOperator(){
      this.operator = null
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

button{
  padding: 10px;
  min-width: 170px;
  height: 80px;
  margin: 10px;
  background-color: #10aeb2;
  color: white;
  font-size: 24px;
  cursor: pointer;
  vertical-align: top;
  border: none;
}
</style>
