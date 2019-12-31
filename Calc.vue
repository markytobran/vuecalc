<template>
  <div>
    <div class="container">
      <div class="app-header">
        <p>{{ title }}</p>
      </div>
      <div class="screen">
        <p v-if="!rightResult">{{ resultStr }}</p>
        <p v-if="rightResult">{{ finalResult}}</p>
      </div>
      <div class="buttons">
        <div>
          <ul class="first_row">
            <li>
              <button @click="restart">C</button>
            </li>
            <li>
              <button>&lt;</button>
            </li>
            <li>
              <button @click="display(divide)">/</button>
            </li>
            <li>
              <button @click="display(multiply)">X</button>
            </li>
          </ul>
        </div>
        <div>
          <ul class="second_row">
            <li>
              <button @click="display(numberSeven)">7</button>
            </li>
            <li>
              <button @click="display(numberEight)">8</button>
            </li>
            <li>
              <button @click="display(numberNine)">9</button>
            </li>
            <li>
              <button @click="display(sub)">-</button>
            </li>
          </ul>
        </div>
        <div>
          <ul class="third_row">
            <li>
              <button @click="display(numberFour)">4</button>
            </li>
            <li>
              <button @click="display(numberFive)">5</button>
            </li>
            <li>
              <button @click="display(numberSix)">6</button>
            </li>
            <li>
              <button @click="display(add)">+</button>
            </li>
          </ul>
        </div>
        <div>
          <ul class="fourth_row">
            <li>
              <button @click="display(numberOne)">1</button>
            </li>
            <li>
              <button @click="display(numberTwo)">2</button>
            </li>
            <li>
              <button @click="display(numberThree)">3</button>
            </li>
            <li>
              <button id="equal" @click="equal">=</button>
            </li>
          </ul>
        </div>
        <div class="row">
          <ul class="fifth_row">
            <li>
              <button @click="display(numberZero)" id="zero">0</button>
            </li>
            <li>
              <button @click="display(dot)">.</button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      title: "Vue.js Calculator",
      rightResult: false,
      rightRestulStr: false,
      resultStr: "0",
      result: [],
      finalResult: 0,
      numberZero: 0,
      numberOne: 1,
      numberTwo: 2,
      numberThree: 3,
      numberFour: 4,
      numberFive: 5,
      numberSix: 6,
      numberSeven: 7,
      numberEight: 8,
      numberNine: 9,
      multiply: "X",
      add: "+",
      divide: "/",
      sub: "-",
      dot: "."
    };
  },
  methods: {
    display(number) {
      // Result reset
      this.result.push(number);
      if (this.resultStr === "0") {
        this.resultStr = "";
        this.resultStr += "" + number + " ";
      } else {
        this.resultStr += "" + number + " ";
      }
    },
    restart() {
      this.result = [];
      this.resultStr = "0";
      this.rightResult = false;
    },
    equal() {
      // simple numbers
      const sign = this.result[1];
      if (sign === "X") {
        this.finalResult = this.result[0] * this.result[2];
        this.rightResult = true;
      } else if (sign === "/") {
        this.finalResult = this.result[0] / this.result[2];
        this.rightResult = true;
      } else if (sign === "+") {
        this.finalResult = this.result[0] + this.result[2];
        this.rightResult = true;
      } else if (sign === "-") {
        this.finalResult = this.result[0] - this.result[2];
        this.rightResult = true;
      }
      // Float Numbers
      if (sign === ".") {
        const sign = this.result[3];
        const floatNumber = parseFloat(this.result[0] + "." + this.result[2]);
        const floatNumberTwo = parseFloat(
          this.result[4] + "." + this.result[6]
        );
        if (sign === "X") {
          this.finalResult = floatNumber * floatNumberTwo;
          this.rightResult = true;
        } else if (sign === "/") {
          this.finalResult = floatNumber / floatNumberTwo;
          this.rightResult = true;
        } else if (sign === "+") {
          this.finalResult = floatNumber + floatNumberTwo;
          this.rightResult = true;
        } else if (sign === "-") {
          this.finalResult = floatNumber - floatNumberTwo;
          this.rightResult = true;
        }
      }
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.container {
  background: black;
  width: 350px;
  height: 475px;
  box-shadow: 10px 5px 5px black;
}

.app-header {
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.5rem;
  margin-left: auto;
  margin-right: auto;
  padding-top: 1px;
}

.screen {
  background: #366600;
  margin: auto;
  width: 90%;
  height: 60px;
  border: 2px solid white;
  display: flex;
  flex-direction: flex-start;
  text-align: center;
  align-items: center;
  margin-top: 10px;
}

.screen p {
  font-size: 1.8rem;
  padding-left: 10px;
  font-family: "Open Sans", sans-serif;
}

.buttons {
  padding: 8px;
}

ul {
  list-style-type: none;
}

button {
  background: white;
  color: black;
  border: none;
  outline: none;
  font-size: 2rem;
  height: 60px;
  width: 70px;
}

#zero {
  width: 155px;
  margin-left: 5px;
}

#equal {
  height: 130px;
}
.row {
  width: 77%;
  margin-bottom: 200px;
}

.first_row,
.second_row,
.third_row,
.fourth_row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  margin-top: 10px;
}

.fourth_row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  margin-top: 10px;
  margin-bottom: 0px;
}
.fifth_row {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

.fourth_row:last-child {
  height: 70px;
}

button:hover {
  background: black;
  color: white;
  border: 2px solid white;
  cursor: pointer;
}
</style>