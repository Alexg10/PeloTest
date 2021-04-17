<template>
  <div class="cursor__container">
    <div class="custom-cursor"></div>
  </div>
</template>

<script>
  import gsap from 'gsap';

  export default {
    methods: {
      cursorAnim(){
          const cursor = document.querySelector('.custom-cursor');
          const pos = { x: window.innerWidth / 2, y: window.innerHeight / 2 };
          const mouse = { x: pos.x, y: pos.y };
          const speed = 0.2;
          const xSet = gsap.quickSetter(cursor, "x", "px");
          const ySet = gsap.quickSetter(cursor, "y", "px");
          gsap.set(cursor, {xPercent: -50, yPercent: -50});
          window.addEventListener("mousemove", e => {
            mouse.x = e.clientX;
            mouse.y = e.clientY;
          });

          gsap.ticker.add(() => {
            const dt = 1.0 - Math.pow(1.0 - speed, gsap.ticker.deltaRatio());
            pos.x += (mouse.x - pos.x) * dt;
            pos.y += (mouse.y - pos.y) * dt;
            xSet(pos.x);
            ySet(pos.y);
          });
      }
    },
    mounted() {
      this.cursorAnim();
    },
  }
</script>

<style lang="scss" scoped>
  .cursor__container{
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 9;
    pointer-events: none;
  }
  .custom-cursor{
    position: absolute;
    background-color: $primary-color;
    width: 15px;
    height: 15px;
    border-radius: 100%;
    z-index: 999;
    transition: 0.5s cubic-bezier(0.75, -1.27, 0.3, 2.33) transform, 0.2 cubic-bezier(0.75, -1.27, 0.3, 2.33) opacity;
    user-select: none;
    pointer-events: none;
    @media screen and (max-width: 680px) {
      display: none;
    }

  }
</style>
