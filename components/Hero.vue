<template>
  <div class="hero">
    <div class="hero__bg">
      <img class="hero__bg__cover" src="/images/hero__bg.jpg" alt="background" ref="heroCover">
      <div class="hero__bg__overlay">
        <div class="container">
          <div class="row">
            <div class="col-lg-6">
              <span class="esperluette">&</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-12 col-lg-6">
          <div class="hero__title title">
            <span ref="heroTitleTop">City</span>
            <span ref="heroTitleBottom">Concrete</span>
          </div>
        </div>
        <div class="col-md-12 col-lg-3 col-lg-offset-2 align-self-center hero__right">
          <p class="hero__content-right">
            Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.
          </p>
          <a class="btn" href="#">
            Let's signup
            <span>
              <svg width="16" height="11" viewBox="0 0 16 11" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M10.4688 9.78125C10.3125 9.65625 10.25 9.46875 10.25 9.25C10.25 9.0625 10.3125 8.875 10.4688 8.75L13.4375 5.75H0.75C0.3125 5.75 0 5.4375 0 5C0 4.59375 0.3125 4.25 0.75 4.25H13.4375L10.4688 1.28125C10.1562 1 10.1562 0.53125 10.4688 0.25C10.75 -0.0625 11.2188 -0.0625 11.5312 0.25L15.7812 4.5C16.0625 4.78125 16.0625 5.25 15.7812 5.53125L11.5312 9.78125C11.2188 10.0938 10.75 10.0938 10.4688 9.78125Z" fill="black"/>
              </svg>
            </span>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  import { gsap } from 'gsap/dist/gsap';

  export default {
    methods : {
      anim() {
        const heroTitleTop = this.$refs.heroTitleTop;
        const heroTitleBottom = this.$refs.heroTitleBottom;
        const heroCover = this.$refs.heroCover;

        [...document.querySelectorAll('.hero__title span')].map(textWrapper => {
          textWrapper.innerHTML = textWrapper.textContent.replace(
            /\S/g,
            "<span class='letter'>$&</span>"
          );
        })

        //Hero intro animation
        var tl = gsap.timeline({delay: 0.9});
        tl.from(heroCover, {scale: 1.2, ease: "power4.inOut", duration: 4}, 'start')
          .from('.letter', { y: 120, opacity: 0, ease: "power4.inOut", stagger: 0.08, duration: 0.8}, 'start')
          .from('.esperluette', {y: 80, opacity: 0, ease: "power4.inOut", duration: 1.4}, '-=3.4')
          .from('.hero__content-right', {y: 80, opacity: 0, ease: "power4.inOut", duration: 1}, '-=3')
          .from('.btn', {y: 80, opacity: 0, ease: "power4.inOut", duration: 1}, '-=2.8');

        //Parallax title effect
        gsap.to(heroTitleTop, {
          scrollTrigger: {
            trigger: '.hero',
            start: "top top",
            endTrigger: '.carousel',
            scrub: true,
          },
          x: -80
        });
        gsap.to(heroTitleBottom, {
          scrollTrigger: {
            trigger: '.hero',
            start: "top top",
            endTrigger: '.carousel',
            scrub: true,
          },
          x: 80
        });
        //Parallax cover effect
        gsap.to(heroCover, {
          scrollTrigger: {
            trigger: '.hero',
            start: "top top",
            endTrigger: '.carousel',
            scrub: true,
          },
          y: 150
        });
      }
    },
    mounted() {
      this.anim();
    }
  }
</script>

<style lang="scss">
.hero{
  display: flex;
  align-items: center;
  position: relative;
  height: 100vh;
  overflow: hidden;
  color: $white;
  .row{
    display: flex;
    align-items: center;
  }
  &__bg{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    &__cover{
      width: 100%;
      height: 100vh;
      object-fit: cover;
    }
    &__overlay{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background-color: #062105;
      opacity: 0.6;
      color: #000;
      mix-blend-mode: multiply;
      span{
        font-size: 645px;
        position: absolute;
        top: -85px;
        right: -52px;
        color: $white;
        mix-blend-mode: lighten;
        font-family: $secondary-font;
    }
      &__clip-path{
        font-size: 300px;
        position: absolute;
        top: 100px;
        left: 100px;

      }
    }
  }
  &__title{
    font-size: 156px;
    line-height: 88px;
    max-width: 720px;
    color: $white;
    span{
      display: inline-block;
      white-space: nowrap;
    }
  }
  &__right{
    transform: translateY(58px);
  }
  &__content-right{
    letter-spacing: 3px;
    line-height: 19px;
    margin-bottom: 24px;
  }
  @media screen and (max-width: 1200px) {
    .row{
      display: block;
    }
  }

  @media screen and (max-width: 680px) {
    .row{
      display: block;
    }
    &__bg{
      &__overlay{
        span{
          font-size: 370px;
          position: absolute;
          top: -9px;
          right: 27px;
        }
      }
    }
    &__title{
      font-size: 86px;
      line-height: 47px;
      margin-bottom: 40px;
      max-width: 540px;
      transform: translateY(0);
    }
    &__right{
      transform: translateY(0);
    }
  }
}

</style>
