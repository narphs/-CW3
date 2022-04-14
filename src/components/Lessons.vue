<template>
  <div class="col-10 pl-0 pr-3">
                            <div class="row">
                                <div class="col-3 mb-3" v-for="product in products" :key="product.id" >
                       <div class="card border-success">
                          
                   
                   
                        <img v-bind:src="product.image" style="height: 200px;">
                     <div class="card-body">
                    <p v-html="product.Location"></p>
                     <h5 class="card-title"  v-text="product.subject"></h5>
                    <p>Price: {{product.price}}</p>
   
                
                    <button v-on:click="addToCart(product)" class="btn btn-block btn-success">
                        add to cart
                        </button>
                    </div>         
    </div>
   </div>
    </div>
   </div>

       

</template>

<script>
export default {
    name: "LessonList",
    props:["products"],
   
    methods: {
      addToCart(product) {
        console.log ('Added lesson', product.id);
        this.$emit('addProduct', product);
      },
      
    },
  };
</script>
