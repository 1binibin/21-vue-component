<template>
  <div class="header-wrapper">  <!-- 감싸주는 div는 한개. 2개 부터 에러 발생 -->
    <h1 class="logo">Hello {{ name }}</h1>
    <button @click="showAlert">눌러봐</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {  // Component는 data가 함수.
    return {
      name: 'wonbin'
    }
  },
  methods: {
    showAlert(e) {
      alert('Hello ' + this.name)
    }
  }
}
</script>

<style lang="scss">
.header-wrapper {
  text-align: center;
  h1.logo {
    color: red;
  }
}
</style>