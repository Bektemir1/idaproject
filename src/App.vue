<template>
 <div class="wrapper">
    <div class="wrapper_form" id="wr">
      <Form v-on:addProduct="addProduct"/>
    </div>
   <div class="overlay" id="overlay"></div>
   <div class="wrapper_catalog" >
     <Catalog
       v-on:deleteProduct="deleteProduct"
       :catalog="catalog"/>
   </div>
 </div>
</template>

<script>
import Catalog from './components/Catalog'
import Form from './components/Form'
export default {
  name: 'App',
  components: {
    Form,
    Catalog
  },
  data () {
    return {
      catalog: JSON.parse(localStorage.getItem('catalog')) || []
    }
  },
  methods: {
    deleteProduct (id) {
      this.catalog = this.catalog.filter((item) => item.id !== id)
      localStorage.setItem('catalog', JSON.stringify(this.catalog))
    },
    addProduct (newProduct) {
      this.catalog.push(newProduct)
      localStorage.setItem('catalog', JSON.stringify(this.catalog))
    }
  }
}
</script>

<style lang="scss">
.wrapper{
  display: flex;
  width:100%;
  &_form{
    width:25%;
  }
  &_catalog{
    width:75%;
  }
}

</style>
