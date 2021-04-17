<template>
  <div>
    <Loader />
    <Header />
    <CustomCursor />
    <div class="main">
      <Nuxt />
    </div>
    <Footer />
  </div>
</template>

<script>
  import Header from '~/components/header/Header'
  import Footer from '~/components/Footer'
  import Loader from '~/components/header/Loader'
  import CustomCursor from '~/components/CustomCursor'

  export default {
    components: {
      Header,
      CustomCursor,
      Loader,
      Footer
    }
  }
</script>
<style lang="scss">
.main{
  margin-bottom: 145px;
}
</style>
