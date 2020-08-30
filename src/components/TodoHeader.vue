<template>
  <header>
      <img class="logo" alt="Vue logo" src="../assets/logo.png">
      <h1>Todo List</h1>
    </header>
</template>

<script>
export default {
  name: 'TodoHeader',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  header {
    display: flex;
    justify-content: center;

    img {
      height: 30px;
      margin: 0 12px;
    }
  }
</style>
