<template>
    <div class="demo-alert-box">
      <slot></slot>
    </div>
</template>

<script>
export default {
  name: 'HelloWorld',
}
</script>

<style lang="scss" scoped>
@import "../assets/sass/variables.scss";

  .demo-alert-box {
    border: 1px solid $primary-text-color;
    max-width: 40%;
    min-height: 150px;
    margin-left: auto;
    margin-right: auto;
    padding-top: 30px;
  }
</style>
