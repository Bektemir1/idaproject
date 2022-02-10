<template>
  <div class="product">
    <div class="product_delete">
      <img src="../assets/img/delete.svg">
    </div>
    <div class="product_img">
      <img src="../assets/img/img.png">
    </div>
    <h2 class="product_title">Product name</h2>
    <p class="product_desc">Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк</p>
    <span class="product_price">4100 руб</span>
  </div>
</template>

<script>
export default {
  name: 'CatalogItem'
}
</script>

<style lang="scss">

.product{
  width:calc(33.33% - 16px);
  margin-left:16px;
  margin-bottom:16px;
  background: #fff;
  padding-bottom: 24px;
  position: relative;
  cursor:pointer;
  &_img{
    width:100%;
    overflow: hidden;
    height:200px;
    img{
      width:100%;
      height:100%;
      transition: 0.4s;

    }
  }
  &_title{
    font-weight: 600;
    font-size:20px;
    padding: 0 16px;
    color:#3f3f3f;
  }
  &_desc{
    font-size:16px;
    color:#3f3f3f;
    padding: 0 16px;
    margin-bottom: 30px;
  }
  &_price{
    font-size:24px;
    font-weight: 600;
    color:#3f3f3f;
    padding: 0 16px;
  }
  &_delete{
    width: 32px;
    height: 32px;
    background: #FF8484;
    border-radius:10px;
    position: absolute;
    top:-8px;
    right:-8px;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity:0;
  }
}
.product:hover .product_img img{
  transform: scale(1.15);

}
.product:hover .product_delete{
  opacity: 1;
  z-index:99;
  transition:1s;
}

@media(max-width:576px){

}
</style>
