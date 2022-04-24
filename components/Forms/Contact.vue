<template>
  <div class="form-wrap">
    <v-snackbar
      :timeout="4000"
      top
      right
      v-model="snackbar"
      class="notification"
    >
      <div class="action">
        Message Sent
      </div>
      <v-btn
        text
        icon
        @click="snackbar = false"
      >
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-snackbar>
    <hidden point="mdUp">
      <div class="logo logo-header">
        <nuxt-link :to="routeLink.medical.home">
          <img :src="logo" alt="logo">
        </nuxt-link>
      </div>
    </hidden>
    <hidden point="smDown">
      <v-btn
        :href="routeLink.medical.home"
        icon
        class="backtohome"
      >
        <i class="ion-ios-home-outline" />
        <i class="ion-ios-arrow-thin-left" />
      </v-btn>
    </hidden>
    <v-container class="max-md">
      <h3 class="use-text-title pb-3 text-center">
        {{ $t('common.contact_title') }}
      </h3>
      <p class="desc use-text-subtitle2 text-center">
        {{ $t('common.contact_subtitle') }}
      </p>
      <div class="form">
        <v-form
          ref="form"
          v-model="valid"
        >
          <v-row class="spacing6">
            <v-col cols="12" sm="6" class="pa-6">
              <v-text-field
                v-model="name"
                :rules="nameRules"
                :label="$t('common.form_name')"
                class="input"
                required
              />
            </v-col>
            <v-col cols="12" sm="6" class="pa-6">
              <v-text-field
                v-model="email"
                :rules="emailRules"
                :label="$t('common.form_email')"
                class="input"
                required
              />
            </v-col>
            <v-col cols="12" sm="6" class="pa-6">
              <v-text-field
                v-model="phone"
                :label="$t('common.form_phone')"
                class="input"
              />
            </v-col>
            <v-col cols="12" sm="6" class="pa-6">
              <v-text-field
                v-model="company"
                :label="$t('common.form_company')"
                class="input"
              />
            </v-col>
            <v-col cols="12" class="pa-6">
              <v-textarea
                v-model="message"
                rows="6"
                class="input"
                :label="$t('common.form_message')"
              />
            </v-col>
          </v-row>
          <div class="btn-area">
            <div class="form-control-label">
              <v-checkbox
                v-model="checkbox"
                color="primary"
                :rules="[v => !!v || 'You must agree to continue!']"
                :label="$t('common.form_terms')"
                required
              />
              <a href="#">
                {{ $t('common.form_privacy') }}
              </a>
            </div>
            <v-btn
              color="primary"
              @click="validate"
              large
            >
              {{ $t('common.form_send') }}
              <v-icon class="right-icon">
                mdi-send
              </v-icon>
            </v-btn>
          </div>
        </v-form>
      </div>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './form-style.scss';
@import '../Title/title-style.scss';
</style>

<script>
import logo from '~/static/images/medical-logo.svg'
import brand from '~/static/text/brand'
import link from '~/static/text/link'
import Hidden from '../Hidden'

export default {
  components: {
    Hidden
  },
  data() {
    return {
      valid: true,
      snackbar: false,
      name: '',
      nameRules: [v => !!v || 'Name is required'],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
      ],
      phone: '',
      company: '',
      message: '',
      checkbox: false,
      logo: logo,
      brand: brand,
      routeLink: link
    }
  },
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    }
  }
}
</script>
