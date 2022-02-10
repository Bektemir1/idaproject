<template>
<div>
 <div class="wrapper_sort">
   <button class="add_product" @click="addClass">+ Добавить товар</button>
   <select class="sort">
     <option>По умолчанию</option>
     <option>Hello</option>
     <option>Hello</option>
   </select>
 </div>
  <div class="catalog_item">
    <CatalogItem/>
  </div>
</div>
</template>

<script>
import CatalogItem from '../components/CatalogItem'
export default {
  name: 'Catalog',
  props: ['catalog'],
  components: {
    CatalogItem
  },

  methods: {
    addClass () {
      const form = document.getElementById('wr')
      form.classList.add('active')
      document.getElementById('overlay').classList.add('active')
    }
  }
}
</script>

<style scoped>
.wrapper_sort{
  display: flex;
  justify-content: flex-end;
  margin-bottom: 16px;
}
.sort{
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  width: 131px;
  color:#b4b4b4;
  height: 36px;
  border:none;
  padding:0 10px;
  appearance: none;
  background: url('../assets/img/arrow.svg')no-repeat;
  background-position-x: 87%;
  background-position-y: 53%;
}
.catalog_item{
  display: flex;
  flex-wrap: wrap;
}
.add_product{
  padding: 10px 15px;
  background: #e9ecff;
  color:#616cf5;
  border:none;
  border-radius:10px;
  cursor:pointer;
  display: none;
  margin-left: 16px;
}
@media(max-width:992px){
  .add_product{
    display: block;
  }
  .wrapper_sort{
    justify-content: space-between;
  }
}
@media(max-width:576px){
  .add_product{
    margin-left: 0;
  }
}
</style>
