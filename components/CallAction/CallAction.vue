<template>
  <fragment>
      <v-container :class="{ 'fixed-width': mdUp }">
        <div class="root">
          <v-card class="paper">
            <v-row align="center" no-gutters>
              <v-col cols="12" md="8">
                <h4 class="display-1 pb-2">
                  {{ $t('medicalLanding.cta_title') }}
                </h4>
                <p>
                  {{ $t('medicalLanding.cta_subtitle') }}
                </p>
              </v-col>
              <v-col cols="12" md="2">
                <v-row align="center" justify="center">
                  <div>
                    <a href=''><img alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png' style="border-radius: 13px; width: 280px; height: 120px;"/></a>

                  </div>
                  <div>
                    <a href="" style="display: inline-block; overflow: hidden; border-radius: 13px; width: 250px; height: 83px;"><img src="https://tools.applemediaservices.com/api/badges/download-on-the-app-store/black/en-us?size=250x83&amp;releaseDate=1344988800&h=d0f9a63b10ac7b51417f4ee15800b22c" alt="Download on the App Store" style="border-radius: 13px; width: 250px; height: 83px;"></a>
                  </div>
                  
                  <!-- <v-btn
                    :href="link.contact"
                    color="primary"
                    class="button"
                  >
                    {{ $t('medicalLanding.cta_btn') }}
                  </v-btn> -->
                </v-row>
              </v-col>
            </v-row>
          </v-card>
        </div>
      </v-container>
    </fragment>
</template>

<style lang="scss" scoped>
@import './action-style.scss';
</style>

<script>
import link from '~/static/text/link'
// import imgPlayStore from '~/static\images\data_rawat\google-play-badge.png'

export default {
  data(){
    return {
      link: link
      // imgPlayStore: imgPlayStore
    }
  },
  computed: {
    mdUp() {
      return this.$mq === 'mdDown' || this.$mq === 'lgDown' || this.$mq === 'xl'
    }
  }
  
}
</script>
