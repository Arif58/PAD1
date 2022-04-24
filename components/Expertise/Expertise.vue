<template>
  <fragment>
    <div class="root">
      <v-container>
        <v-row class="spacing8">
          <v-col cols="12" lg="1" v-if="isDesktop" />
          <v-col cols="12" md="5">
            <div :class="{ 'text-center': !isDesktop}">
              <div class="title-deco">
                <div v-if="isDesktop" class="decoration"></div>
                <title-deco :text="$t('medicalLanding.expertise_title')" />
              </div>
            </div>
            <u-animate-container>
              <u-animate
                :offset="-100"
                name="zoomInShort"
                delay="0.1s"
                duration="0.3s"
                class="parallax-wrap"
              >
                <div class="parallax-wrap" v-if="loaded">
                  <kinesis-container
                     :duration="1500"
                     easing="cubic-bezier(0.23, 1, 0.32, 1)"
                  >
                    <kinesis-element
                      :strength="15"
                      type="translate"
                      tag="div"
                    >
                      <span class="icon-green" />
                    </kinesis-element>
                    <kinesis-element
                      :strength="10"
                      type="translate"
                      tag="div"
                    >
                      <span class="icon-red" />
                    </kinesis-element>
                    <kinesis-element
                      :strength="30"
                      type="translate"
                      tag="div"
                    >
                      <span class="icon-blue" />
                    </kinesis-element>
                  </kinesis-container>
                </div>
              </u-animate>
            </u-animate-container>
          </v-col>
          <v-col
            cols="12"     
            lg="6"
            md="7"
          >
            <!-- <h4 class="title-default use-text-subtitle">
              {{ $t('medicalLanding.expertise_subtitle') }}
            </h4> -->
            <!-- mengubah class yg tadinya use-text-paragraph menjadi use-text-subtitle2 -->
            <!-- <h4 class="title-default use-text-subtitle">
               {{ $t('medicalLanding.expertise_tujuan') }}
            </h4> -->
            <p class="title-default use-text-paragraph">
              {{ $t('medicalLanding.expertise_paragraph') }}
            </p>
            <hidden point="xsDown">
              <div class="running-tag" v-if="loaded">
                <slick :options="slickOptions">
                  <div
                    v-for="(group, indexGroup) in expertiseList"
                    :key="indexGroup"
                    class="tag-group"
                  >
                    <span
                      v-for="(item, indexChild) in group"
                      :key="indexChild"
                      class="tag-item"
                    >
                      {{ item }}
                    </span>
                  </div>
                </slick>
              </div>
            </hidden>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </fragment>
</template>

<style lang="scss" scoped>
@import './expertise-style.scss';
@import '../Title/title-style.scss';
</style>

<script>
import { KinesisContainer, KinesisElement } from 'vue-kinesis'
import TitleDeco from '../Title/WithDecoration'
import Hidden from '../Hidden'

export default {
  components: {
    TitleDeco,
    Hidden,
    KinesisContainer,
    KinesisElement,
    Slick: () => import('vue-slick')
  },
  data() {
    return {
      loaded: false,
      slickOptions: {
        dots: false,
        infinite: true,
        speed: 500,
        centerMode: true,
        arrows: false,
        autoplay: true,
        autoplaySpeed: 3000,
        slidesToShow: 1,
        slidesToScroll: 1,
        vertical: true
      },
      expertiseList: [
        // ['Dentist', 'Padriatic', 'Cardiology'],
        // ['Othopaedi', 'Traumatologi', 'Anestesiologi'],
        // ['Reumatologi', 'Andrologi', 'Ortodonsia'],
        // ['Dentist', 'Padriatic', 'Cardiology'],
        // ['Othopaedi', 'Traumatologi', 'Anestesiologi'],
        // ['Reumatologi', 'Andrologi', 'Ortodonsia'],
        // ['Dentist', 'Padriatic', 'Cardiology'],
        // ['Othopaedi', 'Traumatologi', 'Anestesiologi'],
        // ['Reumatologi', 'Andrologi', 'Ortodonsia']
      ]
    }
  },
  mounted() {
    this.loaded = true
  },
  computed: {
    isDesktop() {
      const lgUp = this.$store.state.breakpoints.lgUp
      return lgUp.indexOf(this.$mq) > -1
    }
  }
}
</script>
