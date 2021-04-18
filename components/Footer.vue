<template>
  <div class="footer">
    <div class="container">
      <div class="row">
        <div class="col-12 footer__content">
          <img class="footer__content__logo" src="/images/pelo_studio.jpg" alt="Pelotest">
          <a href="https://github.com/Alexg10/PeloTest" target="_blank">X Alexg10</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
  .footer{
    background-color: $black;
    color: $white;
    padding: 40px;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    z-index: -1;
    a{
      color: $white;
      font-size: 18px;
    }
    &__content{
      display: flex;
      justify-content: center;
      align-items: center;
      &__logo{
        border-radius: 100%;
        width: 64px;
        margin-right: 12px;
      }
    }
  }

</style>
