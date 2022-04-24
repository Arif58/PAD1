<template>
  <div class="mobile-nav">
    <div
      :class="{ 'menu-open': open }"
      class="menu"
    >
      <v-list
        dense
        tag="nav"
      >
        <v-list-item
          v-for="(item, index) in navMenu"
          :key="index"
          :href="'#' + item"
          link
          :style="{ animationDuration: index * 0.15 + 's' }"
        >
          <v-list-item-content>
            <v-list-item-title class="menu-list">
              {{ $t('medicalLanding.header_'+item) }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
          <!-- <v-btn class="button" href="https://datarawat.com/register" target="_blank" style="margin: 10px;" > 
            {{ $t('medicalLanding.header_register') }}
          </v-btn> -->
          <v-btn class="button" href="https://datarawat.com/login" target="_blank" style="margin: 10px;" > 
              <v-icon left>
                login
              </v-icon>
              <span>
                {{ $t('medicalLanding.header_login') }}
              </span>



            
          </v-btn>
        <!-- <v-list-item
          :href="link.medical.register"
          link
          
        >
          <v-list-item-content>
            <v-list-item-title class="menu-list">
              
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item> -->

        
      </v-list>
      <v-list>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>
                
            </v-list-item-title>
            
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title>
              
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      
    </div>
  </div>
</template>

<style scoped lang="scss">
@import './header-style';
</style>

<script>
import navMenu from './menu'
import link from '~/static/text/link'

export default {
  data() {
    return {
      link: link,
      navMenu: navMenu
    }
  },
  props: {
    open: {
      type: Boolean,
      default: false
    }
  }
}
</script>
