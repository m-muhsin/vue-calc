<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <div class="calculator">
      <div class="display">
        {{ display }}
      </div>
      <div class="buttons">
        <div class="one">
          <button class="delete" @click="del()">DEL</button>
          <button class="clear" @click="clear()">C</button>
        </div>
        <div class="two">
          <button @click="enterNum('7')">7</button>
          <button @click="enterNum('8')">8</button>
          <button @click="enterNum('9')">9</button>
          <button @click="enterSign('/')">/</button>
          <button @click="enterNum('4')">4</button>
          <button @click="enterNum('5')">5</button>
          <button @click="enterNum('6')">6</button>
          <button @click="enterSign('x')">x</button>
          <button @click="enterNum('1')">1</button>
          <button @click="enterNum('2')">2</button>
          <button @click="enterNum('3')">3</button>
          <button @click="enterSign('-')">-</button>
          <button @click="enterNum('.')">.</button>
          <button @click="enterNum('0')">0</button>
          <button @click="enterEqual()">=</button>
          <button @click="enterSign('+')">+</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'calculator',
  data () {
    return {
      msg: 'Calculator',
      display: '',
      temp: 0,
      currentSign: '',
      ans: 0
    }
  },
  methods: {
    enterNum: function (number) {
      if (this.display === '') {
        this.display = number
      } else {
        this.display += number
      }
    },
    del: function () {
      var num = this.display.toString()
      var newNum = num.substring(0, num.length - 1)
      this.display = newNum
    },
    clear: function () {
      this.display = ''
    },
    enterSign: function (sign) {
      this.temp = this.display
      this.currentSign = sign
      this.display = ''
    },
    enterEqual: function () {
      switch (this.currentSign) {
        case '+':
          this.ans = parseFloat(this.temp) + parseFloat(this.display)
          break
        case '-':
          this.ans = parseFloat(this.temp) - parseFloat(this.display)
          break
        case 'x':
          this.ans = parseFloat(this.temp) * parseFloat(this.display)
          break
        case '/':
          this.ans = parseFloat(this.temp) / parseFloat(this.display)
          break
      }
      this.display = this.ans
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

.calculator {
  background-color: #dedede;
  border: 1px solid #dedede;
  width: 20em;
  height: 30em;
  margin: 0 auto;
  text-align: left;
  border-radius: 5px;
}

.display {
  padding: 15px;
  margin: 15px;
  text-align: right;
  font-size: 1.5em;
  background-color: #fefefe;
  height: 1.2em;
}

.buttons {
  display: flex;
  flex-wrap: wrap;
  padding: 10px;
}

.buttons button {
  flex-grow: 1;
  background-color: #00007c;
  font-size: 1.1em;
  color: white;
  width: 3.5em;
  height: 3.5em;
  padding: 5px;
  margin: 5px;
  border-radius: 10px;
}

.one {
  display: flex;
  flex-grow: 1;
}
</style>
