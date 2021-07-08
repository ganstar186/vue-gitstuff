<template>
  <div id="wrap">
    <header>
      <Navbar/>
    </header>

    <router-view/>
    <footer>
      <Footer/>
    </footer>
  </div>
</template>

<style lang="scss">
@import "../node_modules/bootstrap";
</style>

<script>
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";

export default {
  components: {
    Navbar,
    Footer
  },
}
</script>