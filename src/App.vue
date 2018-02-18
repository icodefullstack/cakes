<template lang="pug">
  #app
    h1 {{header}}
    div.row 
      p.row-item {{content}}
      p.row-item {{content}}
      p.row-item {{content}}

</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      header: "Some Title",
      content: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged."
      
    }
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
      @include tablet
        width: 34%
        margin: 32px
      @include desktop
        width: 24%
        margin: 12px
      
    
    

    
</style>
