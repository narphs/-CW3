<template>
  <div id="app">
    <header>
      
      
      <h1>{{sitename}}</h1>
        <div v-if='showProduct'>
          <div class="cart-button">
           <button  @click="showCheckout">{{this.cart.length}}Checkout</button>
          </div>
      <product :products="products"  @addProduct="addToCart"></product>
      
      </div>
          <div v-else>
            <div class="cart-button">
 <button  @click="showCheckout">Back home</button>
 </div>
      <checkout :cart="cart" @removeProduct='removeProduct'></checkout>
      </div>
    </header>
  </div>

</template>

<script>
import product from "./components/Lessons.vue";
import checkout from "./components/checkoutform.vue";

export default {
  name: "App",
  components: {
    product,
    checkout,
  
  },
  data() {
    return {
      sitename: "Lessons",
       cart: [],
       products:[],
     showProduct: true, 
     
    };
  },
  created  () {
        console.log('requesting data from server ...')
        fetch('https://yababa-3145.herokuapp.com/collection/lessons',{
          method: "GET", 
          headers: {
            'Content-Type': 'application/json', 
            'mode' : 'no-cors'
              }
        }).then(response => response.json())
      .then(data => (this.products = data));
                
            },
   methods: {
    showCheckout() {
                   // console.log(this.showProduct);
                    this.showProduct = this.showProduct ? false : true;
                },
                removeProduct(product){
   
  
  this.cart.splice(this.cart.indexOf(product),1)

  },
    addToCart(product) {
      console.log("addLesson event received by the root component.");
      this.cart.push(product);
    },
    cartItemCount () {
        return this.cart.length;
      },
  },
};

</script>
