<template>
  <div class="counter-wrap">
    <v-container class="fixed-width">
      <v-row
        justify="center"
        align="center"
      >
        <v-col md="4">
          <div class="counter-item deco">
            <div class="text">
              <div class="icon">
                <img src="~static/images/data_rawat/keamanan.png" alt="error">
              </div>
              <div class="left">
                 <p class="left">
                {{ $t('medicalLanding.about_clinics') }}
              </p>
              </div>
             
            </div>
          </div>
        </v-col>

         <v-col md="4">
          <div class="counter-item deco">
            <div class="text">
              <div class="icon">
                <img src="~static/images/data_rawat/mudahDigunakan.png" alt="error">
              </div>
              <div class="left">
                <p>
                {{ $t('medicalLanding.about_easy') }}
              </p>
              </div>
              
            </div>
          </div>
        </v-col>

        <v-col md="4">
          <div class="counter-item deco">
            <div class="text">
              <div class="icon">
                <img src="~static/images/data_rawat/digital.png" alt="error">
              </div>
              <div class="left">
                 <p>
                {{ $t('medicalLanding.about_doctor') }}
              </p>
              </div>
             
            </div>
          </div>
        </v-col>
        <v-col md="4">
          <div class="counter-item">
            <div class="text">
              <h2>
                24
              </h2>
              <p >
                {{ $t('medicalLanding.about_hours') }}
              </p>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './counter-style.scss';
</style>
