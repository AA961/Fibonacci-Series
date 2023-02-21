<template>
  <section class="fibonacci-container">
    <div class="flex">
      <h1>Fibonacci Series</h1>
    </div>
    <div class="flex wrapper">
      <label for="num-terms">Enter number of terms:</label>
      <input type="number" id="num-terms" v-model="numTerms" min="1" @input="generateSeries">
    </div>
  
    <div class="series-container">
      <div v-for="(term, index) in series" :key="index" class="term">{{ term }}</div>
    </div>

    <div class="signature flex" v-if="isSign">
      <h5>Theek Ha Mam Jee...?</h5>
    </div>

  </section>

</template>

<script>
export default {
  data() {
    return {
      numTerms: 1,
      series: [0, 1],
      isSign: false
    };
  },
  methods: {
    generateSeries() {
      this.isSign = true;
      const { numTerms } = this;
      let t1 = 0,
        t2 = 1,
        nextTerm;
      const series = [t1, t2];

      for (let i = 2; i < numTerms; i++) {
        nextTerm = t1 + t2;
        t1 = t2;
        t2 = nextTerm;
        series.push(nextTerm);
      }

      this.series = series;
    }
  }
};
</script>

<style scoped lang="scss">
.fibonacci-container {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.series-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-content: center;
  margin: 2rem auto;


}

.term {
  background-color: #ccd6a6;
  font-weight: 600;
  border-radius: 12px;
  width: 450px;
  padding: .6rem 1rem;
  position: relative;
  font-size: 1rem;
  list-style-type: none;
  color: #6c4700;
  transition: all .3s ease-in-out;
  margin: 8px auto;

  &:hover {
    color: #CCD6A6;
    background-color: black;
    scale: 1.1;
  }
}

label {
  font-weight: bold;
  margin-right: 1rem;
}

input {
  padding: 0.5rem;
  border-radius: 3rem;
  border: 2px solid #ccc;
  width: 5rem;
  text-align: center;
  font-size: 1rem;
}




button {
  padding: 0.6rem 1rem;
  width: 350px;
  border-radius: 12px;
  color: #6c4700;
  border: 2px solid;
  outline: none;
  transition: all 0.3s ease-in-out;
  background-color: #DAE2B6;

  @media (max-width:576px) {
    width: 300px;
    padding: 8px 16px;
  }

  &:hover {
    // background-color: transparent;
    background-color: #F7EDDB;

  }
}


h1 {
  font-size: 64px;

  @media (max-width:576px) {
    font-size: 37px;
  }
}

.signature {
  color: black !important;
}

h1,
.result,
.flex {
  color: #99680a;
}
</style>

