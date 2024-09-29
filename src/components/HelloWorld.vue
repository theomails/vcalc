<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div class="boxed calc" style="width:300px;margin:auto">
      <table width="100%">

        <tr>
          <td colspan="4">
            <div class="boxed" style="background-color: lightblue;"> 
              &nbsp; {{ display }}
            </div>
          </td>
        </tr>

        <tr>
          <td v-for="num in [1,2,3]" :key="num" width="25%">
            <div class="boxed" @click="numClick(num)">
              {{ num }}
            </div>
          </td>
          <td width="25%">
            <div class="boxed" @click="opClick('+')">
              +
            </div>
          </td>
        </tr>
        <tr>
          <td v-for="num in [4,5,6]" :key="num" width="25%">
            <div class="boxed" @click="numClick(num)">
              {{ num }}
            </div>
          </td>
          <td width="25%">
            <div class="boxed" @click="opClick('-')">
              -
            </div>
          </td>
        </tr>
        <tr>
          <td v-for="num in [7,8,9]" :key="num" width="25%">
            <div class="boxed" @click="numClick(num)">
              {{ num }}
            </div>
          </td>
          <td width="25%">
            <div class="boxed" @click="opClick('*')">
              *
            </div>
          </td>
        </tr>
        <tr>
          <td >
            <div class="boxed"  @click="clear">
              Clear
            </div>
          </td>
          <td>
            <div class="boxed" @click="numClick(0)">
              0
            </div>
          </td>
          <td width="25%">
            <div class="boxed" @click="eqClick">
              =
            </div>
          </td>
          <td width="25%">
            <div class="boxed" @click="opClick('/')">
              /
            </div>
          </td>
        </tr>

      </table>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      display: '',
      val1: '',
      val2: '',
      operation: ''
    };
  },
  methods:{
    numClick(num){
      if('+-*/'.indexOf(this.display) >= 0){
        this.operation = this.display;
        this.display = '';
      }

      this.display=this.display+num;
    },
    opClick(op){
      this.val1=parseFloat(this.display);
      this.display=op;
    },
    eqClick(){
      this.val2=parseFloat(this.display);
      if(this.operation == '+'){
        this.display = this.val1 + this.val2;
      }else if(this.operation == '-'){
        this.display = this.val1 - this.val2;
      }else if(this.operation == '*'){
        this.display = this.val1 * this.val2;
      }else if(this.operation == '/'){
        this.display = this.val1 / this.val2;
      }
    },
    clear(){
      this.display= '';
      this.val1= '';
      this.val2= '';
      this.operation= '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* { box-sizing: border-box }

.calc{
  font-family: 'Courier New', Courier, monospace;
}
.boxed{
  border: 1px solid black;
  display: inline-block;
  padding: 10px 5px;
  width: 100%;
  background-color: #d3b88c;
  color: black;
  cursor: pointer;
}

.boxed:hover{
  background-color: #e4cea9;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
