<template>
  <div class="calculator">
    <h1>Find the Right Buy-to-Let mortgage for you</h1>
    <p class="mb-25">What Type of a Loan are you looking for? </p>

    <div class="calculator__item">
      <div class="calculator__input">
        <label for="value">Property value</label>
        <input
          id="value"
          type="number"
          v-model="value"/>
      </div>

      <div class="calculator__slider">
        <vue-slider
          ref="value"
          v-model="value"
          tooltip="false"
          :data="values"
        >
        </vue-slider>
      </div>
    </div>

    <div class="calculator__item">
      <div class="calculator__input">
        <label for="amount"/>Loan Amount
        <input
          id="amount"
          type="number"
          v-model="amount"/>
      </div>

      <div class="calculator__slider">
        <vue-slider
          ref="amount"
          v-model="amount"
          tooltip="false"
          :data="countedData"
        ></vue-slider>
      </div>
    </div>
  </div>
</template>

<script>
import vueSlider from 'vue-slider-component';

const prepareValues = () => {
  const data = [];

  for(let i = 30000; i <= 900000; i+=10000) {
    data.push(i);
  }

  for(let j = 1000000; j <= 4000000; j+= 200000) {
    data.push(j);
  }

  return data;
};

const prepareSteps = (limit) => {
  const steps = [];

  for (let i = 1000; i <= limit; i += 1000) {
    steps.push(i);
  }
  return steps;
};

export default {
  name: 'Calculator',
  components: { vueSlider },
  methods:{
    countLoanMaximum(max) {
      return max * 0.8;
    },
    setStep(index) {
      this.amount = this.countedData[index];
    }
  },
  data () {
    return {
      value: 30000,
      MIN: 30000,
      MAX: 4000000,
      values: prepareValues(),
      loanMaximum: this.countLoanMaximum(30000),
      countedData: prepareSteps(24000),
      amount: 1000
    };
  },
  watch: {
    value: function(newValue) {
      this.countedMaximum = this.countLoanMaximum(newValue);
      this.countedData = prepareSteps(this.countedMaximum);
      this.setStep(0);

    }
  }
}
</script>
