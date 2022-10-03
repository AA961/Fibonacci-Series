<template>
  <div class="flex">
    <h1>Tower Of Hanoi Solution</h1>
  </div>
  <div class="flex wrapper">
    <!-- <input type="number" ref="noOfDisks" placeholder="Enter the number of Disks" v-model.number="disks"
      @keypress.enter="this.tower.splice(0, this.tower.length), this.solveTower(this.disks, 'A', 'C', 'B')" max="10"
      min="2"> -->

    <label id="label" for="disk">Choose the number of disk</label>
    <select name="" id="disk" v-model.number="disks"
      v-on:change="this.tower.splice(0, this.tower.length), this.solveTower(this.disks, 'A', 'C', 'B')">
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
      <option value="6">6</option>
      <option value="7">7</option>
      <option value="8">8</option>
      <option value="9">9</option>
      <option value="10">10</option>
    </select>
  </div>
  <!-- <button @click="this.tower.splice(0, this.tower.length), this.solveTower(this.disks, 'A', 'C', 'B')">Calculate
    Steps</button> -->

  <div class="steps flex">
    <h3>Total Steps : {{ this.tower.length }}</h3>
  </div>

  <div class="result ">
    <ul v-for="(step, index) in tower">
      <li v-for="s in step">{{ JSON.stringify(s).split('"').join(' ').substr(0, 10) }}
        <span class="text">{{ JSON.stringify(s).split('"').join(' ').substr(10, 2)
        }}</span>{{ JSON.stringify(s).split('"').join(' ').substr(12, 5) }}
        <span class="text">{{ JSON.stringify(s).split('"').join(' ').substr(17, 2) }}</span>
        {{ JSON.stringify(s).split('"').join(' ').substr(19, 4) }}
        <span class="text">{{ JSON.stringify(s).split('"').join(' ').substr(22, 2) }}</span>
        <span class="checkbox"><input type="checkbox"></span>
      </li>
    </ul>
  </div>

  <div class="signature flex">
    <h5>Project By Ammar Ahmed</h5>
  </div>

</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      tower: [],
      disks: null,
      steps: null
    }
  },
  computed: {

  },
  methods: {
    solveTower(n, fromStick, toStick, usingStick) {

      if (n == 1) {
        this.tower.push([`Move Disk 1 From ${fromStick} to ${toStick}`])
        this.steps++;
        return
      }
      this.solveTower(n - 1, fromStick, usingStick, toStick)
      this.tower.push([`Move Disk ${n} From ${fromStick} to ${toStick}`])
      this.solveTower(n - 1, usingStick, toStick, fromStick, this.steps++)

    }
  },
  // mounted() {
  //   this.$refs["noOfDisks"].focus()
  // },

}
</script>

<style scoped lang="scss">
input {
  padding: 0.6rem 1rem;
  border: 3px solid black;
  border-radius: 6px;
  outline: none;
  font-size: 1rem;
  width: 400px;

  @media (max-width:576px) {
    widows: 300px;
    padding: 8px 16px;
  }
}

.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

#label {
  display: block;
  font-size: 1.4rem;
  font-weight: 600;
  text-transform: capitalize;
}

#disk {
  color: #DFE8CC;
  padding: 0.4rem 0.8rem;
  font-size: 1rem;
  font-weight: bold;
  display: block;
  width: 275px;
  outline: none;
  border: none;
  background: #99680a;
  border-radius: 3px;
  margin-top: 8px;
}

.result {
  @media (max-width:576px) {
    transform: translateX(-16px);
  }

  ul {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    li {
      background-color: #CCD6A6;
      // color: black;
      font-weight: 600;
      border-radius: 12px;
      width: 450px;
      padding: 0.6rem 1rem;
      position: relative;
      font-size: 1rem;
      list-style-type: none;
      color: #6c4700;
      transition: all 0.3s ease-in-out;

      &:hover {
        color: #CCD6A6;
        background-color: black;
        scale: 1.1;
      }

      .text {
        color: #0040ff !important;
        font-size: 1.1rem;
        font-weight: 800;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;

        &:nth-child(even) {
          color: rebeccapurple !important;
        }
      }

      @media (max-width:576px) {
        width: 300px;
        padding: 8px 16px;
      }


      .checkbox {
        position: absolute;
        right: 50%;
        top: 20%;

        &:hover {
          cursor: pointer;

        }

        @media (max-width:576px) {
          right: 30%;
        }


      }
    }
  }
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
    font-size: 32px;
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

