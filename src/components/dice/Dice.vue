<template>
  <div class="dice-holder">
    <div
      class="dice"
      :class="{'show1': number1, 'show2': number2, 'show3': number3, 'show4': number4, 'show5': number5, 'show6': number6}"
    >
      <span class="dice-side">1</span>
      <span class="dice-side">2</span>
      <span class="dice-side">3</span>
      <span class="dice-side">4</span>
      <span class="dice-side">5</span>
      <span class="dice-side">6</span>
    </div>
    number1: {{number1}}
    number2: {{number2}}
    number3: {{number3}}
    number4: {{number4}}
    number5: {{number5}}
    number6: {{number6}}
    <ul>
      <li>
        <button @click="setTrue(1)">1</button>
        <button @click="setTrue(2)">2</button>
        <button @click="setTrue(3)">3</button>
        <button @click="setTrue(4)">4</button>
        <button @click="setTrue(5)">5</button>
        <button @click="setTrue(6)">6</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      number1: false,
      number2: false,
      number3: false,
      number4: false,
      number5: false,
      number6: false
    };
  },
  methods: {
    setTrue: function(diceSide) {
      this.setAllFalse();
      if (diceSide === 1) this.number1 = true;
      if (diceSide === 2) this.number2 = true;
      if (diceSide === 3) this.number3 = true;
      if (diceSide === 4) this.number4 = true;
      if (diceSide === 5) this.number5 = true;
      if (diceSide === 6) this.number6 = true;
    },

    setAllFalse: function() {
      this.number1 = false;
      this.number2 = false;
      this.number3 = false;
      this.number4 = false;
      this.number5 = false;
      this.number6 = false;
    }
  }
};
</script>

<style scoped lang="scss">
.dice-holder {
  width: 200px;
  height: 200px;
  border: 1px solid #ccc;
  margin: 80px;
  perspective: 400px;

  margin: 20% auto;

  .dice {
    // display: flex;
    // border: 1px solid rgb(22, 22, 22);
    // width: 50px;
    // height: 50px;
    width: 200px;
    height: 200px;
    position: relative;
    transform-style: preserve-3d;
    transform: translateZ(-100px);
    // transition: transform 1s;

    .dice-side {
      // display: flex;
      // flex: 0 1 200px;
      // width: 50px;
      // height: 50px;
      // background: grey;
      position: absolute;
      width: 200px;
      height: 200px;
      border: 2px solid black;
      line-height: 200px;
      font-size: 40px;
      font-weight: bold;
      color: black;
      text-align: center;
      transition: transform 2s;
      // background-color: whitesmoke;
      // i {
      //   display: flex;
      //   width: 20px;
      //   height: 10px;
      //   font-size: 2em;
      //   text-align: center;
      //   margin: 0 auto;
      //   margin-top: 40%;
      //   background: chocolate;
      // }

      &:nth-child(1) {
        transform: rotateY(0deg) translateZ(100px);
      }
      &:nth-child(2) {
        transform: rotateY(90deg) translateZ(100px);
      }
      &:nth-child(3) {
        transform: rotateY(180deg) translateZ(100px);
      }
      &:nth-child(4) {
        transform: rotateY(-90deg) translateZ(100px);
      }
      &:nth-child(5) {
        transform: rotateX(90deg) translateZ(100px);
      }
      &:nth-child(6) {
        transform: rotateX(-90deg) translateZ(100px);
      }
    }
    &.show1 {
      transform: translateZ(-100px) rotateY(0deg);
    }
    &.show2 {
      transform: translateZ(-100px) rotateY(-90deg);
    }
    &.show3 {
      transform: translateZ(-100px) rotateY(-180deg);
    }
    &.show4 {
      transform: translateZ(-100px) rotateY(90deg);
    }
    &.show5 {
      transform: translateZ(-100px) rotateX(-90deg);
    }
    &.show6 {
      transform: translateZ(-100px) rotateX(90deg);
    }
  }
}
</style>
