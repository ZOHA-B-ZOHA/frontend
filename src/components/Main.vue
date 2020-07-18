<template>
  <div>
    <div>제목(여기에 캐치프레이즈 랜덤으로)</div>
    <div>게이지 바</div>
    <div>
      <button v-on:click="handleClick">참여하기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  methods: {
    handleClick: function() {
      this.$emit('toggleMain') // 이것보다 더 깔끔한 방법이 없을까...
    }
  }
}
</script>
