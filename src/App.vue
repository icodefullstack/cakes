<template lang="pug">
  #app
    h1 {{city.name}}, {{city.country}}
    div.row 
      p.row-item(v-for="data in weather") {{data.main.temp_min}}&#8451; - {{data.main.temp_max}}&#8451;
        br 
        span at {{data.dt_txt}}
</template>

<script>
  import axios from 'axios';
export default {
  name: 'app',
  data () {
    return {
      header: "Some Title",
      weather:"",
      city: "",
      test: [{name: "test1"},{name: "test2"}]
      
    }
  },
  methods:{
    
  },
  created(){
  axios.get('http://api.openweathermap.org/data/2.5/forecast?q=Dublin,ie&appid=4ef048fafa75365bcbf06efe005cf0ff&units=metric')
    .then((res)=>{
    this.weather = res.data.list;
    this.city = res.data.city;
  })
    .catch()
}
}
</script>

<style lang="sass">
$tablet-width: 768px
$desktop-width: 1024px
@mixin tablet
  @media(min-width: #{$tablet-width})and(max-width: #{$desktop-width - 1})
    @content
@mixin desktop
  @media(min-width: #{$desktop-width})
    @content


html,
body
  margin: 0
  padding: 8px
  background: #dedada
  
  
#app 
  font-family: 'Comfortaa', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  
  display: flex
  flex-direction: column
  flex-wrap: nowrap
  justify-content: flex-start
  border: 1px solid gray
  border-radius: 4px
  box-shadow: 0px 12px 12px -12px gray
  width: 100%
  padding: 16px
  box-sizing: border-box
  @include tablet
    padding: 32px
    width: calc(100%-32px)
  @include desktop
    padding: 64px
    width: calc(100%-64px)
  min-height: 100vh
  background: #fefafa
  color: gray
  h1
    text-align: center
    font-family: 'Oswald', sans-serif
    text-decoration: underline
  .row
    display: flex
    flex-direction: row
    flex-wrap: wrap
    justify-content: space-around
    .row-item
      width: 100%
      margin: 8px
      padding: 16px
      border: 1px solid gray
      border-radius: 4px
      box-shadow: 0px 12px 12px -12px gray
      font-size: 32px
      background: #eef
      @include tablet
        width: 34%
        margin: 32px
      @include desktop
        width: 24%
        margin: 12px
      span
        font-size: 24px
        font-family: 'Oswald', sans-serif
        color: #ace
    
    

    
</style>
