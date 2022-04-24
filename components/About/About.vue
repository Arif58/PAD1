<template>
  <div class="root">
    <v-container class="fixed-width">
      <v-row>
        <v-col cols="12" md="5" class="pa-6">
          <div class="text-center">
            <title-deco :text="$t('medicalLanding.about_title')" :bg="photo"/>
          </div>
        </v-col>
        <v-col cols="12" md="7" class="pa-6">
          <h4 class="title-default use-text-subtitle">
            {{ $t('medicalLanding.about_subtitle') }}
          </h4>
          
          <!-- <blockquote>
            {{ $t('medicalLanding.about_quote') }}
          </blockquote> -->
          <!-- mengubah tulisan penjelasan menjadi normal -->
          <p class="title-default use-text-paragraph">
              {{ $t('medicalLanding.about_quote') }}
            </p>
          <counter />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './about-style';
@import '../Title/title-style';
</style>

<script>
import imgAPI from '~/static/images/data_rawat/tentang.jpg' //mengubah gambar
import Counter from '../Counter'
import TitleDeco from '../Title/WithDecoration'

export default {
  data() {
    return {
      photo: imgAPI
    }
  },
  components: {
    Counter,
    TitleDeco
  },
  computed: {
    isDesktop() {
      const lgUp = this.$store.state.breakpoints.lgUp
      return lgUp.indexOf(this.$mq) > -1
    }
  }
}
</script>
