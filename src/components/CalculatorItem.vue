<template>
  <div class="calculator">
   <div class="display">{{current || '0'}}</div>
   <div @click="clear" class="button">C</div>
   <div @click="sign" class="button">+/-</div>
   <div @click="percentage" class="button">%</div>
   <div @click="divide" class="button operator">÷</div>
   <div @click="append('7')" class="button">7</div>
   <div @click="append('8')" class="button">8</div>
   <div @click="append('9')" class="button">9</div>
   <div @click="times" class="button operator">x</div>
   <div @click="append('4')" class="button">4</div>
   <div @click="append('5')" class="button">5</div>
   <div @click="append('6')" class="button">6</div>
   <div @click="minus" class="button operator">-</div>
   <div @click="append('1')" class="button">1</div>
   <div @click="append('2')" class="button">2</div>
   <div @click="append('3')" class="button">3</div>
   <div @click="plus" class="button operator">+</div>
   <div @click="append('0')" class="button zero">0</div>
   <div @click="dot" class="button">.</div>
   <div @click="equal" class="button operator">=</div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null
    }
  },

  methods: {
    clear() {
      this.current = '';
    },

    sign(){
      this.current = String(this.current);
      this.current = this.current.includes('-') ? this.current.replace('-', '') :
      this.current === '0' ? this.current :
      this.current = '-' + this.current;
    },

    percentage(){
      this.current = parseFloat(this.current) / 100;
    },

    append(number) {
      this.current = this.current + number;
    },

    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.')
      }
    },

    divide() {
      this.operator = (a, b) => a / b;
    },

    times() {
      this.operator = (a, b) => a * b;      
    },

    minus() {
      this.operator = (a, b) => a - b;
    },

    plus() {
      this.operator = (a, b) => a + b;
    },

    equal() {

    }
  }
}
</script>

<style lang="scss" scoped>

  * {
    margin: 0;
    padding: 0;
  }

  .calculator {
    font-size: 40px;
    width:  600px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);

    .display {
      color: #eee;
      grid-column: 1 / 5;
      background-color: #0F0F0F;
      text-align: left;
      padding: 0 0 0 10px;
    }

    .button {
      background-color: #eee;
      border: 1px solid;
      cursor: pointer;
    }

    .zero {
      grid-column: 1 / 3;
    }

    .operator {
      background-color: #7CCFAA;
    }
  }
</style>