<template>
  <div class="calculator">
    <h1>Find the Right Buy-to-Let mortgage for you</h1>
    <p>What Type of a Loan are you looking for? </p>

    <div>
      <label for="value">Property value</label>
      <input id="value" type="number"/>
    </div>
    <div>
      <vue-slider ref="value" v-model="value"></vue-slider>
    </div>

    <div>
      <label for="amount"/>Loan Amount
      <input id="amount" type="number"/>
    </div>
    <div>
      <vue-slider ref="amount" v-model="amount"></vue-slider>
    </div>
  </div>
</template>

<script>
import vueSlider from 'vue-slider-component';

export default {
  name: 'Calculator',
  components: { vueSlider },
  data () {
    return {
      value: 0,
      amount: 0
    };
  }
}
</script>
