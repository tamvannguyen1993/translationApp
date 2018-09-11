<template>
  <div class="row" id="translateForm">
    <div class="md6 offset-md3">
    <form class="well" @submit="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="Enter a word"/>
      <select v-model="language">
        <option value="ru">Russian</option>
        <option value="es">Spainish</option>
        <option value="fr">France</option>
        <option value="zh">Chinese</option>
      </select>
      <input class="btn btn-primary" type="submit" value="Translate" />
    </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate: '',
      language: ''
    }
  },
  created() {
    this.language = 'ru'
  },
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault();
    }
  }

}
</script>

<style>
</style>
