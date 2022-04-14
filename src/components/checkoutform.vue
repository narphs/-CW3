<template>
<main>

 <div>
   <ul class="list-group">
   <li class="list-group-item" v-for='product in cart' :key="product.id">
      <div class="row">
        <div class="col-4">
        <img style="height: 100px;" v-bind:src="product.image" />
         </div>
                                    <div class="col-6">
                                        <p>{{product.subject}}</p>
                                    </div>
                                    <div class="col-2">
                                        <span style="cursor: pointer;" class="text-danger" v-on:click='remove(product)'>remove ><b>x</b></span>
                                    </div>
                            </div>
                     </li>
              </ul>
       </div>
 </main>
 
</template>
<script>
export default {
  name: "checkout-page",
  props: ['cart'],
  data() {
    return {
}; 

},
methods: {
     remove(product) {
        this.$emit('removeProduct', product)
     }},

}
</script>
