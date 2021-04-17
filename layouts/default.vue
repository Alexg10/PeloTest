<template>
  <div>
    <Loader />
    <Header />
    <CustomCursor />
    <Nuxt />
  </div>
</template>

<script>
  import Header from '~/components/header/Header'
  import Loader from '~/components/header/Loader'
  import CustomCursor from '~/components/CustomCursor'

  export default {
    components: {
      Header,
      CustomCursor,
      Loader
    }
  }
</script>
