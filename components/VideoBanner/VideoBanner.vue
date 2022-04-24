<template>
  <div class="hero-content">
    <hidden point="smUp">
      <figure class="mobile-cover">
        <img
          :src="cover"
          alt="cover"
        >
      </figure>
    </hidden>
    <v-container :class="{ 'fixed-width': mdUp }">
      <v-row>
        <v-col cols="12" md="6">
          <div class="banner-text">
            <div class="title">
              <h3 class="text-helper use-text-title">
                {{ $t('medicalLanding.banner_title') }}
              </h3>
            </div>
            <h5 class="subtitle use-text-subtitle2">
              {{ $t('medicalLanding.banner_subtitle') }}
            </h5> 
            <!-- ini search field ngga ke pake -->
            <!-- <v-card class="search-banner">  -->
              <!-- <v-text-field
                :label="isMobile2 ? 'Search...' : 'Search doctor, medicines or clinic...'"
                class="search"
                hide-details
                filled
              /> -->
              <div class="action">
                
                <v-btn v-if="isMobile" class="button" style="padding : 20px; margin: 10px;" href="https://datarawat.com/register" target="_blank">
                  <v-icon left>
                    how_to_reg
                  </v-icon>
                  <span>
                    {{ $t('medicalLanding.header_register') }}
                  </span>
                  <!-- {{ $t('medicalLanding.header_register') }} -->
                  <span v-if="isDesktop">
                    
                  </span>
                </v-btn>
              </div>
            <!-- </v-card> -->
          </div>
        </v-col>
        <v-col
          v-if="isTablet"
          md="6"
          cols="12"     
          class="pa-6 visual-content"
        >
          <div class="deco-banner">
            <div class="menu-bg">
            </div>
            <div class="video-bg"></div>
          </div>
          <div class="video-wrap">
            <div class="video-figure">
              <div class="inner-figure">
                <hidden point="mdDown">
                  <v-btn
                    v-if="play"
                    fab
                    text
                    class="btn-play"
                    @click="togglePause()"
                  >
                    <v-icon v-if="playCtrl">mdi-pause</v-icon>
                    <v-icon v-else>mdi-play</v-icon>
                  </v-btn>
                </hidden>
                <img
                  v-if="!play || isMobile "
                  :src="cover"
                  alt="cover"
                >
                <div
                  v-if="yt.use"
                  class="video"
                >
                  <youtube
                    v-if="isDesktop"
                    :video-id="videoId"
                    :player-vars="playerVars"
                    :width= "1080"
                    :height="720"
                    ref="youtube"
                    @playing="playing"
                    @ended="ended"
                  />
                </div>
              </div>
            </div>
          </div>
          <div class="parallax-banner">
            <dots-parallax />
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './banner-style.scss';
</style>

<script>
import imgAPI from '~/static/images/imgAPI'
import DotsParallax from '../Parallax/Dots'
import youtube from '~/youtube'
import Hidden from '../Hidden'

export default {
  components: {
    Hidden,
    DotsParallax
  },
  data() {
    return {
      videoId: 'sbef4EWb4js', /* ini untuk ambil video video dari yt */
      playerVars: {
        autoplay: 1,
        controls: 0,
        rel: 0,
        showinfo: 0,
        mute: 1,
        origin: 'http://localhost:8009'
      },
      yt: youtube,
      play: false,
      playCtrl: true,
      cover: imgAPI.medical[0]
    }
  },
  methods: {
    playing() {
      this.play = true
      this.playCtrl = true
    },
    ended() {
      this.player.playVideo()
    },
    togglePause() {
      this.playCtrl = !this.playCtrl
      if (this.playCtrl) {
        this.player.playVideo()
      } else {
        this.player.pauseVideo()
      }
    }
  },
  computed: {
    player() {
      return this.$refs.youtube.player
    },
    mdUp() {
      return this.$mq === 'mdDown' || this.$mq === 'lgDown' || this.$mq === 'xl'
    },
    isDesktop() {
      const lgUp = this.$store.state.breakpoints.lgUp
      return lgUp.indexOf(this.$mq) > -1
    },
    isTablet() {
      const smUp = this.$store.state.breakpoints.smUp
      return smUp.indexOf(this.$mq) > -1
    },
    isMobile() {
      const mdDown = this.$store.state.breakpoints.mdDown
      return mdDown.indexOf(this.$mq) > -1
    },
    isMobile2() {
      const xsDown = this.$store.state.breakpoints.xsDown
      return xsDown.indexOf(this.$mq) > -1
    }
  }
}
</script>
