<template>
  <div class="container">
    <div class="content">
      <header class="align">
        <div>
          <div id="textDay" class="texto">D A Y</div>
          <input id="day" class="estilo" type="text" v-model="day" @blur="validateDay">
          <span id="errorMessage1" class="align3">{{ errorMessage1 }}</span>
        </div>
        <div>
          <div id="textMonth" class="texto">M O N T H</div>
          <input id="month" class="estilo" type="text" v-model="month" @blur="validateMonth">
          <span id="errorMessage2" class="align3">{{ errorMessage2 }}</span>
        </div>
        <div>
          <div id="textYear" class="texto">Y E A R</div>
          <input id="year" class="estilo" type="text" v-model="year" @blur="validateYear">
          <span id="errorMessage3" class="align3">{{ errorMessage3 }}</span>
        </div>
      </header>
      <div class="alinhar">
        <hr class="linha-personalizada">
        <button id="button" class="botao" @click="calculateAge"><img src="@/assets/icon-arrow.svg" alt="Calculate"></button>
      </div>
      <div>
        <div class="align4">
          <div id="displayYear" class="letra2">{{ calculatedYear }}</div>
          <div class="letra">years</div>
        </div>
        <div class="align2">
          <div id="displayMonth" class="letra2">{{ calculatedMonth }}</div>
          <div class="letra">months</div>
        </div>
        <div class="align5">
          <div id="displayDay" class="letra2">{{ calculatedDay }}</div>
          <div class="letra">days</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AgeCalculator',
  data() {
    return {
      day: '',
      month: '',
      year: '',
      errorMessage1: '',
      errorMessage2: '',
      errorMessage3: '',
      calculatedYear: '--',
      calculatedMonth: '--',
      calculatedDay: '--'
    };
  },
  methods: {
    validateDay() {
      const day = parseInt(this.day);
      const maxDaysInMonth = [31, this.isLeapYear() ? 29 : 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
      const month = parseInt(this.month) - 1;
      if (day < 1 || day > maxDaysInMonth[month]) {
        this.errorMessage1 = 'Must be a valid date';
      } else {
        this.errorMessage1 = '';
      }
    },
    validateMonth() {
      const month = parseInt(this.month);
      if (month < 1 || month > 12) {
        this.errorMessage2 = 'Must be a valid month';
      } else {
        this.errorMessage2 = '';
      }
    },
    validateYear() {
      const year = parseInt(this.year);
      if (year > new Date().getFullYear()) {
        this.errorMessage3 = 'Must be in the past';
      } else {
        this.errorMessage3 = '';
      }
    },
    isLeapYear() {
      const year = parseInt(this.year);
      return (year % 4 === 0 && year % 100 !== 0) || year % 400 === 0;
    },
    calculateAge() {
      this.validateDay();
      this.validateMonth();
      this.validateYear();

      if (this.errorMessage1 || this.errorMessage2 || this.errorMessage3) {
        return;
      }

      const valueDay = parseInt(this.day);
      const valueMonth = parseInt(this.month) - 1;
      const valueYear = parseInt(this.year);
      const inputDate = new Date(valueYear, valueMonth, valueDay);
      const today = new Date();

      const differenceInMilliseconds = today - inputDate;
      const differenceInDays = Math.floor(differenceInMilliseconds / (1000 * 60 * 60 * 24));

      this.calculatedYear = Math.floor(differenceInDays / 365);
      this.calculatedMonth = Math.floor((differenceInDays % 365) / 30);
      this.calculatedDay = Math.floor((differenceInDays % 365) % 30);
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f2f2f2;
  padding: 60px;
}

.content {
  background-color: #ffffff;
  border-radius: 20px 20px 200px 20px;
}

.alinhar {
  display: flex;
  justify-content: center;
  align-items: center;
}

.linha-personalizada {
  background-color: hsl(0, 0%, 94%);
  margin-right: 0px;
  margin-left: 50px;
  height: 2px;
  width: 600px;
  border: none;
}

.align {
  border: none;
  box-sizing: border-box;
  margin-top: 50px;
  margin-left: 50px;
  gap: 30px;
  display: flex;
  justify-content: flex-start;
}

.estilo {
  width: 120px;
  height: 60px;
  border-radius: 5px;
  font-size: 32px;
  padding-left: 25px;
  border-color: hsl(0, 0%, 94%);
  cursor: pointer;
  font-family: 'Poppins-ExtraBold', sans-serif;
}

.color1 {
  border-color: hsl(259, 100%, 65%);
}

.texto {
  margin-bottom: 10px;
  font-family: 'Poppins-Bold', sans-serif;
  color: hsl(0, 1%, 44%);
  font-size: 15px;
}

.botao {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  margin-right: 50px;
  background-color: hsl(259, 100%, 65%);
  color: #fff;
  border: none;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.letra {
  font-size: 90px;
  font-family: 'Poppins-ExtraBoldItalic', sans-serif;
}

.letra2 {
  color: hsl(259, 100%, 65%);
  font-size: 82px;
  font-family: 'Poppins-ExtraBold', sans-serif;
}

.align2,
.align4,
.align5 {
  border: none;
  box-sizing: border-box;
  margin-top: -30px;
  gap: 10px;
  display: flex;
  margin-right: 200px;
  margin-left: 60px;
  justify-content: flex-start;
}

.align3 {
  border: none;
  box-sizing: border-box;
  margin-top: 10px;
  gap: 50px;
  display: flex;
  justify-content: flex-start;
  color: hsl(0, 100%, 67%);
  font-family: 'Poppins-Italic', sans-serif;
}

.highlight-border {
  font-family: 'Poppins-ExtraBold', sans-serif;
  border-color: hsl(0, 100%, 67%);
  color: hsl(0, 100%, 67%);
}

.mousebotao1 {
  background-color: hsl(259, 100%, 65%);
}

.mousebotao2 {
  background-color: hsl(0, 0%, 8%);
}

.mousetexto2 {
  border-color: hsl(259, 100%, 65%);
}

.mousetexto1 {
  border-color: hsl(0, 0%, 94%);
}
</style>
