<template>
  <div id="app">
    <h1>スペルチェッカーアプリ</h1>
    <SpellChecker></SpellChecker>
  </div>
</template>

<script>
import SpellChecker from './components/SpellChecker.vue';

export default {
  name: 'App',
  components: {
    SpellChecker
  }
};
</script>
