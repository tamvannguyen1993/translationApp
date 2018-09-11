<template>
  <div  class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5 class="text-muted">Powered By Vue.js</h5>
    <hr />
    <TranslateForm @formSubmit="translateText"></TranslateForm>
    <TranslatedOutput :translatedText="translatedText"></TranslatedOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslatedOutput from './components/TranslatedOutput'
export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslatedOutput
  },
  data() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180911T161036Z.dba055575e7c50f3.1cbe1027c7f4f92d68ac74054794e89bd1830082&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      })
    }
  }
}
</script>

<style>
body {
  background:#fefefe;
}

</style>
