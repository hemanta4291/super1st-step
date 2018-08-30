<template>
  <div id="app">
   

    <div class="container">
    
    <Navbar @searchone="search"></Navbar>

      <div class="row">
        <div class="col-sm-9">
         <Inven @adtoevent="addcaart" :items="items"></Inven>

        </div>
        <div class="col-sm-3">
          <Card @itemremove="removeitem(index)" :items="cart"></Card>
        </div>
      
      </div>

    
    
    </div>
  </div>
</template>

<script>
import Navbar from './components/navbar'
import Inven from './components/inventory'
import Card from './components/card'
import data from './data.js'

export default {
  name: 'App',
  components:{
    Navbar,
    Inven,
    Card
  },
  data(){
    return {
      items: [],
      cart:[]
    }
  },
  mounted(){
    this.items=data
  },
  methods:{
    search(keyword){
      this.items=data.filter(item =>{
        return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !==-1
      })
    },

    addcaart(item){
      this.cart.push(item);
    },
    removeitem(index){
      this.cart.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
