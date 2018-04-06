<template>
<div>
    <my-header>
        <h1>Связь между компонентами Vue.js</h1>
        <h2 slot='subtitle'>Слот / slot</h2>
    </my-header>
    <div class="container">    
        <products></products>
        <div>
            <span @click="mode=(mode== 'view' ? 'add' : 'view')">Mode: {{mode}}</span>
            <keep-alive>
                <component :is="componentName"></component>
            </keep-alive>
        </div>
    </div>
</div>
</template>

<script>
import ProductsList from './ProductsList.vue'
import ProductDetails from './ProductDetails.vue'
import myHeader from './Header.vue'
import ProductService from './ProductService.js'
import ProductAdd from './ProductAdd.vue'

export default {
  data(){
    return {
      products: [],
      mode: 'view'
    }
  },
  computed: {
      componentName() {
          return this.mode == 'view' ? 'ProductDetails' : 'ProductAdd';
      }
  },
  components: {
    myHeader,
    'products': ProductsList,
    ProductDetails,
    ProductAdd
  }
}
</script>

<style>
  .container{
    display:flex;
    align-items:flex-start;
  }

</style>