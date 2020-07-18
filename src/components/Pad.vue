<template>
  <div>
    <div>
      <label for="quantity">구매 수량</label>
      <br />
      <!-- <input id="quantity" name="" type="number" value="1" min="1" /> -->
      <p>{{ quantity }}</p>
      <div v-on:click="handleQuantity">
        <button value="increase">+</button>
        <button value="decrease">-</button> <!-- 이거 하이픈 기호 말고 빼기 기호 쓰기!!!! -->
      </div>
      <br />
      <label for="phone">휴대폰 번호</label>
      <br />
      <!-- <input id="phone" name="" type="tel" pattern="" required value={{ phoneNumber }} /> -->
      <!-- v-on:click="handleClick" -->
      <p>{{ phoneNumber }}</p>
      <div id="keypad" v-on:click="handlePhoneNumber">
        <button value="1">1</button>
        <button value="2">2</button>
        <button value="3">3</button>
        <button value="4">4</button>
        <button value="5">5</button>
        <button value="6">6</button>
        <button value="7">7</button>
        <button value="8">8</button>
        <button value="9">9</button>
        <button value="delete">입력취소</button>
        <button value="0">0</button>
        <button value="submit">적립/확인</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Pad',
  props: {
    branch: String,
  },
  data: function() {
    return {
      quantity: 1,
      phoneNumber: ''
    }
  },
  methods: {
    handleQuantity: function(e) {
      const value = e.target.value
      if (value === 'increase') {
        this.quantity++
      } else if (value === 'decrease') {
        if (this.quantity > 1) this.quantity--
      } else {
        console.error('invalid value')
      }
    },
    handlePhoneNumber: function(e) { // 아 이벤트 객체를 그대로 받는구나! 아님 똑같이 구현한 건가
      const value = e.target.value
      if (Number(value) >= 1 && Number(value) <= 9) {
        this.phoneNumber += e.target.value
      } else if (value === 'delete') {
        this.phoneNumber = this.phoneNumber.slice(0, -1)
      } else if (value === 'submit') {
        // 지점 정보, 수량, 전화번호를 백엔드에 제출
        this.$emit('toggleMain')
      } else {
        console.error('invalid value')
      }
    }
  }
}
</script>

<style scoped>
#keypad {
  width: 300px;
  height: 200px;
  display: grid;
  grid-template-rows: repeat(4, 1fr);
  grid-template-columns: repeat(3, 1fr);
}
</style>
