<template>
  <q-layout view="lHh Lpr lFf">
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL, LocalStorage } from 'quasar'
import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'MyLayout',
  // data () {
  //   return {
  //     lang: this.$i18n.locale,
  //   }
  // },
  // computed:{
  //     ...mapGetters('systemConfig', ['languages', 'currentLanguage'])
  // },
  // watch: {
  //   lang (lang) {
  //     this.$i18n.locale = this.lang;

  //     let curLang = this.lang
  //     let langObj = this.languages.find(x => x.value === curLang)
  //     this.setLanguage(langObj)

  //     import(`quasar/lang/${this.lang}`).then(language => {
  //       this.$q.lang.set(language.default)
  //     })
  //   }
  // // },
  // methods: {
  //   ...mapActions('systemConfig', ['setLanguage'])
  // },
  // mounted() {
  //   let defaultLanguage = "zh-hant"
  //   this.$i18n.locale = defaultLanguage
  //   this.lang = defaultLanguage
  // }
}
</script>

<style>
</style>
