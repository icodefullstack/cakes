<template lang="pug">
  #app
    h1 Waracle Cakes
    
    div#editform Load a cake here to edit or input your data to create a new one.
      br
      input(v-model="cakedata.id" class="myinput")
      input(v-model="cakedata.name" class="myinput")
      input(v-model="cakedata.comment" class="myinput")
      input(v-model="cakedata.imageUrl" class="myinput" )
      input(v-model="cakedata.yumFactor" class="myinput")

      p
        button(@click="updateCake(cakedata.id)") Update
        button(@click="createCake()") Create
    
    div.row 
      div.row-item(v-for="cake in cakes") 
        h3 {{cake.name}}
        p {{cake.comment}}
        img(:src="cake.imageUrl") 
        p
          button(@click="getCake(cake.id)") Load for Edit
          button(@click="deleteCake(cake.id)") delete
       
</template>


<script>
  import axios from 'axios';
export default {
  name: 'app',
  data () {
    return {
      cakes:"",
      cakedata:{
        id:"",
        name:"",
        comment:"",
        imageUrl:"",
        yumFactor:0
      }
    }
  },
  methods:{
    getCake(id){
    axios.get('http://ec2-52-209-201-89.eu-west-1.compute.amazonaws.com:5000/api/cakes/'+id)
    .then((res)=>{
      
    this.cakedata = res.data;
  })
    .catch()
    },
    updateCake(id){
      console.log(this.cakedata)
      axios.put('http://ec2-52-209-201-89.eu-west-1.compute.amazonaws.com:5000/api/cakes/'+id, this.cakedata)
    .then((res)=>{
      
    console.log(res)
  })
    .catch()
    },
    deleteCake(id){
      console.log(this.cakedata)
      axios.delete('http://ec2-52-209-201-89.eu-west-1.compute.amazonaws.com:5000/api/cakes/'+id)
    .then((res)=>{
      
    console.log(res)
  })
    .catch()
    },
    createCake(){
      console.log(this.cakedata)
      axios.post('http://ec2-52-209-201-89.eu-west-1.compute.amazonaws.com:5000/api/cakes/')
    .then((res)=>{
      
    console.log(res)
  })
    .catch()
    }
    
  },
  created(){
  axios.get('http://ec2-52-209-201-89.eu-west-1.compute.amazonaws.com:5000/api/cakes')
    .then((res)=>{
    this.cakes = res.data;
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
      font-size: 16px
      background: #eef
      @include tablet
        width: 34%
        margin: 32px
      @include desktop
        width: 24%
        margin: 12px
      span
        font-size: 12px
        font-family: 'Oswald', sans-serif
        color: #ace
      img
        width: 100%
        height: auto
  #editform
    border: 1px solid gray
    border-radius: 8px
    padding: 32px
    .myinput
      display: block
      padding: 8px
      margin: 4px -8px
      border-radius: 4px
      border: 1px solid #5b637b
      width: 100%
      
      

    
</style>
