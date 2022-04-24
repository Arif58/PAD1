<template>
  <div>
    <div class="main-wrap">
      <main-header />
      <div class="container-wrap">
        <oval-top />
        <section id="home">
          <video-banner />
        </section>
        <section
          id="about"
          class="space-top-short"
        >
          <about />
        </section>
        <dots-parallax />      
        <section
          id="facility"
          class="space-top"
        >
          <facilities />
        </section>
        <section
          id="our-expertise"
          :class="[isTablet ? 'space-top-short' : 'space-top']"
        >
          <expertise />
        </section>
        
        <section class="space-top-short" id="call-to-action">
          <call-action />
        </section>
        <section class="space-top-short" id="clinics">
          <clinics />
        </section>
      </div>
      <hidden point="mdDown">
        <page-nav />
      </hidden>
      <main-footer />
      <hidden point="mdDown">
        <notification />
      </hidden>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '~/assets/styles';

@function section-margin($margin) {
  @return $margin * 20;
}
.main-wrap {
  position: relative;
  width: 100%;
  overflow: hidden;
  @include palette-text-primary;
  .theme--dark & {
    background-color: $dark-background-default;
  }
  .theme--light & {
    background-color: $light-background-paper;
  }
}
.space-top {
  margin-top: section-margin($spacing1);
  @include breakpoints-down(md) {
    margin-top: section-margin(6px);
  }
  @include breakpoints-down(xs) {
    margin-top: section-margin($spacing1 / 2);
  }
}
.space-bottom-short {
  margin-bottom: section-margin($spacing1 / 2);
}
.space-top-short {
  margin-top: section-margin($spacing1 / 2);
}
.container-wrap {
  @include breakpoints-up(md) {
    margin-top: $spacing6;
  }
  section {
    position: relative;
  }
}
</style>

<script>
import Header from '~/components/Header'
import VideoBanner from '~/components/VideoBanner'
import About from '~/components/About'
import Facilities from '~/components/Facilities'
import Expertise from '~/components/Expertise'
import Testimonials from '~/components/Testimonials'
import AskDoctors from '~/components/AskDoctors'
import CallAction from '~/components/CallAction'
import Clinics from '~/components/Clinics'
import Footer from '~/components/Footer'
import Hidden from '~/components/Hidden'
import PageNav from '~/components/PageNav'
import Notification from '~/components/Notification'
import DotsParallax from '~/components/Parallax/Dots'
import OvalTop from '~/components/Parallax/OvalTop'
import brand from '~/static/text/brand'

export default {
  components: {
    'main-header': Header,
    DotsParallax,
    OvalTop,
    VideoBanner,
    About,
    Facilities,
    Expertise,
    Testimonials,
    AskDoctors,
    CallAction,
    Clinics,
    PageNav,
    Hidden,
    Notification,
    'main-footer': Footer
  },
  computed: {
    isTablet() {
      return this.$mq === 'mdDown' || this.$mq === 'smDown' || this.$mq === 'xsDown' // eslint-disable-line
    },
    isMobile() {
      return this.$mq === 'smDown' || this.$mq === 'xsDown'
    }
  },
  head() {
    return {
      title: brand.medical.name + ' - Home Page'
    }
  }
}
</script>
