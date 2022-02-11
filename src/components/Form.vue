<template>
<div class= "form">
  <h2 class="form_title">Добавление товара</h2>
  <div class="form_inputs">
    <label>Наименование товара <span class="req"></span></label>
    <input :class="{active: val_name}" v-model="newProduct.name" placeholder="Введите наименование товара">
    <span v-if="val_name" class="form_inputs_validation">Поле является обязательным</span>
    <label>Описание товара </label>
    <textarea v-model="newProduct.description" placeholder="Введите описание товара"></textarea>
    <label>Ссылка на изображение товара <span class="req"></span></label>
    <input :class="{active: val_img}"  v-model="newProduct.img" placeholder="Введите ссылку">
    <span v-if="val_img" class="form_inputs_validation">Поле является обязательным</span>
    <label>Цена товара <span class="req"></span></label>
    <input  :class="{active: val_price}"  v-model="newProduct.cost" placeholder="Введите цену">
    <span v-if="val_price" class="form_inputs_validation">Поле является обязательным</span>
    <button class="form_inputs_add" @click="addProduct">Добавить товар</button>
    <button class="form_inputs_cancel" @click="removeClass()">Закрыть</button>
  </div>
  <div class="form_success" id="success">
      <span>Product has been added</span>
  </div>
</div>
</template>

<script>
export default {
  name: 'Form',
  data () {
    return {
      val_name: false,
      val_desc: false,
      val_img: false,
      val_price: false,
      newProduct: {
        id: Date.now(),
        name: '',
        description: '',
        img: '',
        cost: ''
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
      this.val_name = false
      this.val_price = false
      this.val_img = false
    },
    addProduct () {
      if (this.newProduct.name === '') {
        this.val_name = true
      } else {
        this.val_name = false
      }
      if (this.newProduct.img === '') {
        this.val_img = true
      } else {
        this.val_img = false
      }
      if (this.newProduct.cost === '') {
        this.val_price = true
      } else {
        this.val_price = false
      }
      if (!this.val_name && !this.val_img && !this.val_price) {
        document.getElementById('success').classList.add('active')
        setTimeout(() => {
          document.getElementById('success').classList.remove('active')
        }, 2000)
        this.removeClass()
        this.$emit('addProduct', this.newProduct)
        this.newProduct = {
          id: Date.now(),
          name: '',
          description: '',
          img: '',
          cost: ''
        }
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
  overflow:auto;
  &_success.active{
    top:10px;
  }
  &_success{
    position:fixed;
    padding:20px 50px;
    background: #7BAE73;
    top:-80px;
    border-radius:10px;
    z-index:999;
    color:#fff;
    right:10px;
    transition: 0.4s;

  }
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
      border:1px solid transparent;
      margin-bottom: 16px;
      padding-left:10px;
      font-size:14px;
      box-sizing:border-box;
    }
    input.active{
      border-color:#ff8484;
    }
    textarea{
      height: 100px;
      resize: none;
      padding-top: 12px;
    }
    label{
      color:#49485E;
      font-size:14px;
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
    &_validation{
      font-size:12px;
      color:#ff8484;
      display: block;
      margin-bottom: 5px;
      margin-top: -10px;
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
