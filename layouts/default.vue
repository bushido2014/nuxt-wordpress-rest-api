<template>
  <div>
    <Header />
    <transition name="fade" mode="out-in">
      <Nuxt />
    </transition>
    <Footer />

    <div class="back">
      <BackToTop />
    </div>
  </div>
</template>
<script>
import Header from '~/components/Header';
import Footer from '~/components/Footer';
import BackToTop from '~/components/BackToTop.vue';
export default {
  components: {
    Header,
    Footer,
    BackToTop,
  },
};
</script>
