<template>
  <div class="root">
    <div class="carousel-handle">
      <div v-if="loaded" class="carousel-wrap">
        <slick
          ref="slick"
          :options="slickOptions"
        >
          <div class="item">
            <div class="carousel-prop">
              <div />
            </div>
          </div>
          <div
            v-for="(item, index) in facilityList"
            :key="index"
            class="item"
          >
            <card
              :title="item.title"
              :desc="item.desc"
              :img="item.img"
              :button="$t('medicalLanding.services_button')"
            />
          </div>
          <div class="item">
            <div class="carousel-prop">
              <div />
            </div>
          </div>
        </slick>
      </div>
    </div>
    <div class="floating-title">
      <v-container class="fixed-width">
        <div class="title">
          <title-icon
            :text="$t('medicalLanding.services_title')"
            icon="library_add"
            extended
          />
          <nav class="arrow">
            <v-btn
              fab
              small
              aria-label="next"
              class="margin"
              @click="next()"
            >
              <v-icon>mdi-arrow-left</v-icon>
            </v-btn>
            <v-btn
              fab
              small
              aria-label="prev"
              class="margin"
              @click="prev()"
            >
              <v-icon>mdi-arrow-right</v-icon>
            </v-btn>
          </nav>
        </div>
      </v-container>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './facilities-style.scss';
</style>

<script>
import imgLogo1 from '~/static/images/data_rawat/stetoskop2.jpg'  //menambah gambar layanan1
import imgLogo2 from '~/static/images/data_rawat/stetoskop.jpg' //menambah gambar layanan2
import imgLogo3 from '~/static/images/data_rawat/data.jpg' //menambah gambar layanan 3
import imgLogo4 from '~/static/images/data_rawat/kasur.jpg'  //menambah gambar layanan1
import Card from '../Cards/Default'
import TitleIcon from '../Title/WithIcon'

export default {
  components: {
    Card,
    TitleIcon,
    Slick: () => import('vue-slick')
  },
  data() {
    return {
      loaded: false,
      slickOptions: {
        dots: false,
        infinite: false,
        speed: 500,
        slidesToShow: 4,
        arrows: false,
        slidesToScroll: 1,
        variableWidth: true,
        responsive: [
          {
            breakpoint: 1100,
            settings: {
              slidesToShow: 4
            }
          },
          {
            breakpoint: 800,
            settings: {
              slidesToShow: 2
            }
          }
        ]
      },
      facilityList: [
        {
          title: 'Data Resume',
          desc:
            'Sistem integrasi transfer data Resume Medis User',
          img: imgLogo1
        },
        {
          title: 'lntegrasi Sistem',
          desc:
            'Integrasi sistem Informasi Manajemen layanan kesehatan',
          img: imgLogo2
        },
         {
          title: 'Manajemen Data',
          desc:
            'Manajemen data dari pasien dan tentunya menggunakan prinsip kerahasian',
          img: imgLogo3
        },
         {
          title: 'Pendaftaran Pasien',
          desc:
            'Pendaftaran pasien mulai dari rawat jalan, rawat inap, dan IGD',
          img: imgLogo4
        }
       
      ]
    }
  },
  mounted() {
    this.loaded = true
    const props = window.innerWidth > 1400 ? 1 : 2 // div.carousel-props length for screen < 1400px and (-1) for screen > 1400px
    const lastSlide = Math.floor(this.facilityList.length + props - this.slickOptions.slidesToShow)
    setTimeout(() => {
      if (window.innerWidth > 1200 && !this.$vuetify.rtl) {
        this.$refs.slick.goTo(lastSlide)
      }
    }, 100)
  },
  methods: {
    next: function() {
      this.$refs.slick.next()
    },
    prev: function() {
      this.$refs.slick.prev()
    }
  }
}
</script>
