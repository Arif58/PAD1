<template>
  <div class="main-wrap">
    <decoration />
    <contact />
  </div>
</template>

<style scoped lang="scss">
.main-wrap {
  position: relative;
  .theme--dark & {
    background-color: $dark-background-default;
  }
  .theme--light & {
    background-color: $light-background-paper;
  }
}
</style>

<script>
import Contact from '~/components/Forms/Contact'
import Decoration from '~/components/Forms/Decoration'
import brand from '~/static/text/brand'

export default {
  components: {
    Contact,
    Decoration
  },
  head() {
    return {
      title: brand.medical.name + ' - Contact'
    }
  }
}
</script>
