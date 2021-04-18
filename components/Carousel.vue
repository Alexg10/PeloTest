<template>
  <div class="carousel" @mousemove="parallax">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <slick-slide
            ref="slick"
            class="carousel__content"
            :options="slickOptions"
            @afterChange="handleAfterChange"
            @beforeChange="handleBeforeChange"
          >
            <div v-for="(item, index) in items" :key="index" class="carousel__item">
              <div class="carousel__item__illu" v-html="item.ico" ref="itemIllu"/>
              <div class="carousel__item__title title" v-html="item.title" ref="itemTitle"/>
              <div class="carousel__item__content" v-html="item.content" ref="itemContent"/>
            </div>
          </slick-slide>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { gsap } from 'gsap/dist/gsap';
  import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';

  export default {
    data() {
      return {
        slickOptions: {
            slidesToShow: 1,
            arrows: true,
            speed: 800,
            fade: true,
            prevArrow: '<div class="carousel__prev"><svg width="100" height="200" viewBox="0 0 100 200" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M1 1L100 100L1 199" stroke="black"/></svg></div>',
            nextArrow: '<div class="carousel__next"><svg width="100" height="200" viewBox="0 0 100 200" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M1 1L100 100L1 199" stroke="black"/></svg></div>',
        },
        items: [
          {
            ico:'<svg id="illu_0" width="175" height="70" viewBox="0 0 175 70" fill="none" xmlns="http://www.w3.org/2000/svg"><g clip-path="url(#clip01)"><path class="green__path" d="M87.0869 27.3981C48.9905 27.3981 24.2452 41.3146 16.6346 48.2729C21.5271 55.4486 42.4671 69.8 87.0869 69.8C131.707 69.8 151.342 55.4486 155.582 48.2729C148.624 41.3146 125.183 27.3981 87.0869 27.3981Z" fill="#C6FFAB" stroke="#C6FFAB"/><circle cx="94.2626" cy="48.9252" r="20.8748" stroke="black"/><circle cx="106.005" cy="43.7065" r="7.82804" stroke="black"/><path d="M86.4346 20.2224V0M61.972 20.2224L51.2084 2.93551M42.0757 27.072L27.3981 14.6776M21.5271 36.857L7.50187 32.943M10.7636 48.9252H0M110.571 20.2224L124.27 0M130.467 27.072L147.428 14.6776M151.016 36.857L162.432 32.943M162.432 48.9252H174.5" stroke="black"/></g><defs><clipPath id="clip01"><rect width="174.5" height="69.8" fill="white"/></clipPath></defs></svg>',
            title:'Find out Secret places',
            content:'Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.'
          },
          {
            ico: '<svg id="illu_1" width="204" height="82" viewBox="0 0 204 82" fill="none" xmlns="http://www.w3.org/2000/svg"><g clip-path="url(#clip02)"><ellipse class="green__path" cx="135.5" cy="41" rx="21.5" ry="41" fill="#C6FFAB"/><ellipse cx="110.5" cy="41" rx="21.5" ry="41" stroke="black"/><ellipse class="green__path" cx="85.5" cy="41" rx="21.5" ry="41" fill="#C6FFAB"/><ellipse cx="52.5" cy="41" rx="21.5" ry="41" stroke="black"/><path d="M170.5 45H203.5M50.5 45H0" stroke="black"/></g><defs><clipPath id="clip02"><rect width="203.5" height="82" fill="white"/></clipPath></defs></svg>',
            title:'Discover a new culture',
            content:'Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Sed posuere consectetur est at lobortis. Donec sed odio dui.'
          },
          {
            ico: '<svg id="illu_2" width="200" height="95" viewBox="0 0 200 95" fill="none" xmlns="http://www.w3.org/2000/svg"><g clip-path="url(#clip0)"><path class="green__path" d="M157 72.1429C159.357 72.1429 173.034 82 173.034 82L171.212 70.4896C187.976 66.4537 200 55.4782 200 42.5714C200 26.2396 180.748 13 157 13C133.252 13 114 26.2396 114 42.5714C114 58.9033 133.252 72.1429 157 72.1429Z" fill="#C6FFAB"/><path d="M118.5 14.5H94.5L99.5 49.5H113.5L118.5 14.5Z" stroke="black"/><path d="M107 81C103.766 81 85 94.5 85 94.5L87.5 78.7357C64.4975 73.2084 48 58.1767 48 40.5C48 18.1325 74.4152 -4.0033e-06 107 -2.57897e-06C139.585 -1.15465e-06 166 18.1325 166 40.5C166 62.8675 139.585 81 107 81Z" stroke="black"/><ellipse cx="107" cy="60" rx="9" ry="4" stroke="black"/><path d="M48 74.0157L31.5115 94M31.5115 44.4094H0M41.4046 14.8031L15.0229 0M31.5115 28.8661L12.8244 22.5748M37.7405 60.3228L18.687 68.8346" stroke="black"/><path d="M87.5 79L88 75" stroke="black"/></g><defs><clipPath id="clip0"><rect width="200" height="94.5" fill="white"/></clipPath></defs></svg>',
            title:'Create new stories to tell',
            content:'Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit.'
          }
        ]
      }
    },
    methods: {
      parallax() {
        document.body.onmousemove = event => {
          let halfW = ( document.documentElement.clientWidth / 2 );
          let halfH = ( document.documentElement.clientHeight / 2 );
          let coorX = ( halfW - ( event.pageX - document.documentElement.offsetLeft ) );
          let coorY = ( halfH - ( event.pageY - document.documentElement.offsetTop ) );
          let degX  = ( ( coorY / halfH ) * 6 ) + 'px';
          let degY  = ( ( coorX / halfW ) * -6 ) + 'px';
          [...document.querySelectorAll('.green__path')].map( greenPath => {
            greenPath.style.transform = "translate( "+ degX +", "+ degY +")";
          })
        }
      },
      anim() {
        //Carousel fadeIn animation
        const anim = gsap.from(".carousel__content", {
          opacity: 0,
          duration: 1.5
        });
        ScrollTrigger.create({
          trigger: ".carousel",
          start: "150px bottom",
          animation: anim
        });
      },
      handleAfterChange() {
        //Carousel intro animation before change
        var tl = gsap.timeline();
        tl.fromTo(this.$refs.itemIllu, {y: 40, opacity: 0}, {y: 0, opacity: 1, duration: 0.4, ease: "power4.inOut"});
      },
      handleBeforeChange(){
        //Carousel outro animation before change
        var tl = gsap.timeline();
        tl.to(this.$refs.itemIllu, {y: -20, opacity: 0, duration: 0.2, ease: "power4.inOut"});
      },
      keySlide(e) {
        //Control slider with keyboard
        var vm = this;
        document.onkeydown = function(e){
            e = e || window.event;
            if (e.keyCode == '38') {
                vm.$refs.slick.prev();
            }
            else if (e.keyCode == '40') {
                vm.$refs.slick.next();
            }
            else if (e.keyCode == '37') {
                vm.$refs.slick.prev();
            }
            else if (e.keyCode == '39') {
                vm.$refs.slick.next();
            }
        }
      },
    },
    mounted() {
      this.parallax();
      this.anim();
      this.keySlide();
    },
  }
</script>

<style lang="scss" scoped>
.carousel{
  position: relative;
  background-color: $secondary-color;
  padding: 84px 0;
  &__content{
    max-width: 1020px;
    margin: 0 auto;
  }
  &__item{
    font-size: 54px;
    text-align: center;
    max-width: 600px;
    margin: 0 auto;
    &__illu{
      min-height: 120px;
      margin-bottom: -30px;
      svg{
        overflow: visible;
      }
    }
    &__title{
      margin-bottom: 16px;
    }
    &__content{
      font-size: 24px;
    }
  }
  @media screen and (max-width: 680px) {
    &__item{
      max-width: 80%;
      &__illu{
        margin-bottom: 0;
      }
      &__title{
        font-size: 2.375rem;
      }
      &__content{
        font-size: 1.125rem;
      }
    }
  }
}

</style>
