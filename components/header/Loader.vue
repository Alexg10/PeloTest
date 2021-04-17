<template>
  <div class="loader">
    <div class="loader__content"></div>
  </div>
</template>

<script>
  import gsap from 'gsap'
  export default {
    methods: {
      animLoader() {
        //Anim intro loader
        var tl = gsap.timeline({delay: 0.2});
        tl.to('.loader__content',{y: "-100%", ease: "power4.inOut", duration: 1.2}, 'start')
          .to('.loader',{ y:"-100%", ease: "power4.inOut", duration: 1}, '-=0.8');
      }
    },
    mounted() {
      this.animLoader();
    },
  }
</script>

<style lang="scss" scoped>
  .loader{
    background-color: $white;
    position: fixed;
    width: 100vw;
    height: 100vh;
    z-index: 99;
    &__content{
      position: absolute;
      width: 100vw;
      height: 100vh;
      background-color: $primary-color;
    }
  }
</style>
