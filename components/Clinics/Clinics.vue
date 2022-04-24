<template>
  <div class="root">
    <div class="parallax-bottom">
      <parallax-oval />
    </div>
    <v-container class="fixed-width">
      <v-row class="spacing6">
        <v-col cols="12" lg="1" class="pa-6" v-if="isDesktop" />
        <v-col cols="12" lg="5" md="6" class="pa-6">
          <h4 class="title-primary mt-10">
            {{ $t('medicalLanding.clinic_title') }}
          </h4>
          <div class="block">
            <u-animate-container>
              <!-- menambah key -->
              <div v-for="(item, index) in clinicData"
              :key="index">
                <u-animate
                  :offset="-50"
                  :delay="(index * 0.3) + 's'"
                  name="fadeInLeftShort"
                  duration="0.3s"
                >
                  <AddressCard
                    :name="item.name"
                    :phone="item.phone"
                    :email="item.email"
                    :address="item.address"
                  />
                </u-animate>
              </div>
            </u-animate-container>
          </div>
        </v-col>
        <v-col cols="12" md="6" class="pa-6"> 
          <v-card class="map">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d57360.76366599341!2d106.7973327480584!3d-6.212469870922052!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69f148a2f9e9dd%3A0x302ae5df1a546941!2sSenayan%20Trade%20Center%20(STC)%2C%20Jl.%20Asia%20Afrika%20No.1-41%2C%20RT.1%2FRW.3%2C%20Gelora%2C%20Kecamatan%20Tanah%20Abang%2C%20Kota%20Jakarta%20Pusat%2C%20Daerah%20Khusus%20Ibukota%20Jakarta%2010270!5e0!3m2!1sid!2sid!4v1632319610091!5m2!1sid!2sid" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
            <!-- <GMap
              ref="gMap"
              :cluster="{options: {styles: clusterStyle}}"
              :center="{lat: locations[1].lat, lng: locations[1].lng}"
              :options="{fullscreenControl: false}"
              :zoom="6"
            >
              <GMapMarker
                v-for="location in locations"
                :key="location.id"
                :position="{lat: location.lat, lng: location.lng}"
              />
            </GMap> -->
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './clinics-style.scss';
@import '../Title/title-style.scss';
</style>

<script>
import ParallaxOval from '../Parallax/Oval'
import AddressCard from '../Cards/Address'

export default {
  components: {
    ParallaxOval,
    AddressCard
  },
  data() {
    return {
      clinicData: [
        {
          name: 'PT. Jenius Teknologi Indonesia',
          phone: '+62859106539635',
          email: 'info.datarawat@gmail.com',
          address: 'Senayan Trade Center Lt. 2 | Unit 1046-1047 Jl. Asia Afrika No. 1, Jakarta Pusat 10270'
        }
      ]
      // currentLocation: {},
      // locations: [
      //   {
      //     lat: -6.227725,
      //     lng: 106.798779
      //   },
      //   {
      //     lat: 47.815,
      //     lng: 15.9819
      //   },
      //   {
      //     lat: 40.953076,
      //     lng: 16.21
      //   },
      //   {
      //     lat: 44.22,
      //     lng: 16.98
      //   }
      // ],
      // clusterStyle: [
      //   {
      //     url:
      //       'https://maps.gstatic.com/mapfiles/api-3/images/spotlight-poi2.png',
      //     width: 56,
      //     height: 56,
      //     textColor: '#fff'
      //   }
      // ]
    }
  },
  computed: {
    isDesktop() {
      const lgUp = this.$store.state.breakpoints.lgUp
      return lgUp.indexOf(this.$mq) > -1
    }
  }
}
</script>
