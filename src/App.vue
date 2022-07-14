<template>
  <div class="calculator">
    <div class="result">{{answer}}</div>
    <div class="input">{{inputLog + Input}}</div>

    <div @click="clear()" class="btn operator">C</div>
    <div @click="plusminus()" class="btn operator">+/-</div>
    <div @click="percent()" class="btn operator">%</div>
    <div @click="divide()" class="btn operator">/</div>

    <div @click="addInput('7')" class="btn">7</div>
    <div @click="addInput('8')" class="btn">8</div>
    <div @click="addInput('9')" class="btn">9</div>
    <div @click="multiplication()" class="btn operator">X</div>

    <div @click="addInput('4')" class="btn">4</div>
    <div @click="addInput('5')" class="btn">5</div>
    <div @click="addInput('6')" class="btn">6</div>
    <div @click="subtraction()" class="btn operator">-</div> 

    <div @click="addInput('1')" class="btn">1</div>
    <div @click="addInput('2')" class="btn">2</div>
    <div @click="addInput('3')" class="btn">3</div>
    <div @click="plus()" class="btn operator">+</div>

    <div @click="addInput('0')" class="btn zero">0</div>
    <div @click="decimal()" class="btn">.</div>
    <div @click="equal()" class="btn operator1">=</div> 


  </div>
</template>

<script>

export default {
  data(){
    return{
      Input:'',
      answer:'',
      inputLog:'',
      operator: true,
    }
  },
  methods:{
    addInput(number){
      if(this.operator){
        this.Input=''
        this.operator=false
      }
      this.Input = `${this.Input}${number}`
      
    },
    clear(){
      this.Input=''
      this.inputLog=''
    },
    plus(){
      this.addToInputLog('+')
    },
    divide(){
      this.addToInputLog('/')
    },
    subtraction(){
      this.addToInputLog('-')
    },
    multiplication(){
      this.addToInputLog('*')
    },
    addToInputLog(operator){
      if(this.operator === false){
        this.inputLog += `${this.Input}${operator}`
        this.Input=''
        this.operator=true
      }
    },
    equal(){
      if(this.operator===false){
        this.answer = eval(this.inputLog + this.Input)
      }
    },
    plusminus(){
      if(this.Input!==''){
        this.Input = this.Input.charAt(0) === "-" ? this.Input.slice(1) : `-${this.Input}`
      }
    },
    percent(){
      if(this.Input!==''){
        this.Input = `${parseFloat(this.Input) / 100}`
      }
    },
    decimal(){
      if(this.Input.indexOf('.')===-1){
        this.addInput('.')
      }
    }
  }
  
}
</script>

<style>

body{
  background-color: #FFA07A;
  font-family: 'Roboto', sans-serif;
}
.calculator{
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: 50px 50px;
  background-color: black;
  grid-gap: 10px;
  width: 250px;
  height: 500px;
  padding: 20px;
  border-radius: 20px;
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  margin: auto;
  }

  .btn{
    background-color: #FFA07A;
    color: white;
    width: 40px;
    height: 30px;
    border-radius: 30px;
    text-align: center;
    padding-top:10px;
    margin: 10px;
    font-weight: bolder;
    font-size: 18px;
  }

    .operator{
    background-color: #D4AC0D;
  }

      .operator1{
    background-color: #FF0000;
    font-weight: bolder;

  }

  .result, .input{
    grid-column: span 4;
    font-size: 40px;
    color:white;
    text-align: right;
  }

  .zero{
  grid-column: span 2;
  width: 100px;
}
</style>
