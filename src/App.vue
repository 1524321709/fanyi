<template>
  <div id="app" class="container" >
    <h1>在线翻译</h1>
    <h5 class="lead">简单 / 方便 / 便捷</h5>
    <translateForm v-on:fromSub="translateText"></translateForm>
    <translateOutPlay v-text="translatedText"></translateOutPlay>
  </div>
</template>

<script>
import translateForm from './components/translateForm'
import translateOutPlay from './components/translateOutPlay'

export default {
  name: 'App',
  data(){
    return{
      translatedText:""
    }
  },
  components: {
    translateForm,translateOutPlay
  }, 
  methods: {
    translateText(text,language){
      // alert(text)
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190528T012152Z.6672c997742b17a7.44e3572aed6250480dd53bf459c280df348115da&lang='+language+'&text='+text)
      .then((res)=>{
        // console.log(res.body.text[0])
        this.translatedText = res.body.text[0];
      })
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
