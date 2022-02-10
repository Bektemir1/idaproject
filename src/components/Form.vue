<template>
<div class="form">
  <h2 class="form_title">Добавление товара</h2>
  <div class="form_inputs">
    <label>Наименование товара <span class="req"></span></label>
    <input v-model="newProduct.name" placeholder="Введите наименование товара">
    <label>Описание товара <span class="req"></span></label>
    <textarea v-model="newProduct.description" placeholder="Введите описание товара"></textarea>
    <label>Ссылка на изображение товара <span class="req"></span></label>
    <input v-model="newProduct.img" placeholder="Введите ссылку">
    <label>Цена товара <span class="req"></span></label>
    <input v-model="newProduct.price" placeholder="Введите цену">
    <button class="form_inputs_add" @click="addProduct">Добавить товар</button>
    <button class="form_inputs_cancel" @click="removeClass()">Закрыть</button>
  </div>

</div>
</template>

<script>
export default {
  name: 'Form',
  data () {
    return {
      newProduct: {
        name: '',
        description: '',
        img: '',
        price: ''
      }
    }
  },
  methods: {
    removeClass () {
      const form = document.getElementById('wr')
      form.classList.remove('active')
      setTimeout(() => {
        document.getElementById('overlay').classList.remove('active')
      }, 500)
    },
    addProduct () {
      this.$emit('addProduct', this.newProduct)
      this.newProduct = {
        name: '',
        description: '',
        img: '',
        price: ''
      }
    }
  }
}
</script>

<style lang="scss">
.form_title{
  font-size:28px;
  color:#3f3f3f;
  margin-top:0;
  margin-bottom: 16px;
  height:36px;

}
.form{

  &_inputs{
    padding:24px;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    background: #fff;
    input,textarea{
      width:100%;
      background: #FFFEFB;
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
      border-radius: 4px;
      height:36px;
      border:none;
      margin-bottom: 16px;
      padding-left:10px;
      font-size:12px;
      box-sizing:border-box;
    }
    textarea{
      height: 100px;
      resize: none;
      padding-top: 12px;
    }
    label{
      color:#49485E;
      font-size:12px;
      margin-bottom: 5px;
      display: block;
    }
    .req{
      height: 4px;
      width: 4px;
      margin-bottom: 5px;
      margin-left: 2px;
      background: #ff8484;
      display: inline-block;
      border-radius:50%;
    }
    button{
      border-radius: 10px;
      height: 36px;
      border:none;
      width:100%;
      margin-top: 8px;
      color:#fff;
      cursor:pointer;
      transition: 0.4s;
      border:1px solid transparent;
    }
    &_cancel{
      background: #ff8484;
      display: none;
    }
    &_add{
      background: #7BAE73;
    }
    &_add:hover{
      background: #fff;
      color:#7bae73;
      border-color:#7bae73;
    }
    &_cancel:hover{
      background: #fff;
      color:#ff8484;
      border-color:#ff8484;
    }
  }
}

</style>
