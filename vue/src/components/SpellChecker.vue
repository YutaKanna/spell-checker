<template>
    <div>
      <textarea v-model="inputText"></textarea>
      <button @click="checkSpelling">スペルをチェック</button>
      <div v-if="errorMessage" class="error-message">{{ errorMessage }}</div>
    </div>
</template>
  
<script>
  import axios from 'axios';
  export default {
    data() {
      return {
        inputText: '',
        errorMessage: ''
      };
    },
    methods: {
      async checkSpelling() {
        try {
          const response = await axios.get('https://api.textgears.com/spelling', {
            params: {
              text: this.inputText,
              language: 'en-US',
              key: env.KEY
            }
          });

          const { data } = response;
          console.log(data.response.errors);
          if (data.response.errors && data.response.errors.length > 0) {
            console.log("スペルに誤りがあります。修正してください。");
            this.errorMessage = 'スペルに誤りがあります。修正してください。';
          } else {
            console.log("スペルに誤りはありません。");
            this.errorMessage = 'スペルに誤りはありません。';
          }
        } catch (error) {
          console.error(error);
        }
      }
    }
  };
</script>
  