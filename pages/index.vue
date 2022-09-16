<template>
  <div>
    <Nav/>
    <HomeCarousel :sale_items="sale_items"/>
    <br><br>
    <v-container>
      <h1 class="text-md-h4 text-h6">Our Best Sellers!!</h1>
      <br>
      <ProductSlider :products="products"/>
      <br><br><br>
      <Newletter/>
    </v-container>
    <Footer/>
    <Scrolltop/>
  </div>
</template>

<script>
import Scrolltop from '~/components/Scrolltop.vue';
export default {
  components: { Scrolltop },
async created(){
  this.sale_items = await this.$content('products').where({onSale:true}).fetch();
  this.products = await this.$content('products').fetch();
},
data(){
  return{
    products: null,
    sale_items: null,
  }
}
}
</script>

<style>

</style>