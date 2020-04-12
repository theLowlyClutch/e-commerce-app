<template>
   <div>
Order {{this.$root.$data.value+1}}
<table class="table table-striped table-hover">
<thead>
    <th>Product</th>
    <th>Product picture</th>
    <th>Product option</th>
    <th>Price</th>
    <th>Quantity</th>
    <th>Total</th>
   
</thead>
<tbody>
    <tr v-for="(item, index) in orders[$root.$data.value].items" :key="item">
        
        <td>{{productById(orders[$root.$data.value].items[index].productId).title}}</td>
        <td><img v-bind:src="orders[$root.$data.value].items[index].optionImage"  class="image2"></td>
        <td>{{orders[$root.$data.value].items[index].optionCode}} </td>
        <td>{{orders[$root.$data.value].items[index].price}}</td>
        <td>{{orders[$root.$data.value].items[index].qnt}}</td>
        <td>{{orders[$root.$data.value].items[index].total}}</td>
        
</tr>
    
</tbody>

</table>

   </div>
   
</template>

<script>
import axios from "axios";
export default {
  name: 'Order',
   mounted(){
        axios
      .get("https://euas.person.ee/user/orders" )
      .then (response => {
          this.orders = response.data;
      }),
      axios
      .get("https://euas.person.ee/products/" )
      .then (responsedd => {
          this.products = responsedd.data;
      })
    },
    data: function(){
        return {
            orders:[],
            products: {},
        }
    },
    methods: {
        productById(productId) {
            return this.products.find(product => product.id == productId)
        },
    }
}
</script>


<style scoped>
.image2{
    width: 60px;
    height:60px;
    cursor:pointer;
}
</style>