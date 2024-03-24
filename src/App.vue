<template>
  <AddProduct></AddProduct>
  <h1 style="text-align: center; border:3px; background-color:hsl(192, 82%, 78%); border: 1px solid #ccc;
  border-color: #3608ed;border-width:3px
  ">DISPLAYING THE PRODUCTS DETAIL</h1>
<ul class="item" v-for="item in list" :key="item.id">
  <div class="lis">
  <li class="re"> ITEM ID => {{item.id}}</li>
  <li class="re">ITEM TITLE => {{item.title}}</li>
  <li class="re">ITEM DESCRIPTION => {{item.description}}</li>
  <li class="re">ITEM PRICE => {{item.price}}</li>
  <li class="re">ITEM BRAND=> {{item.brand}}</li></div>
  
  <div class="im" v-if="item.images">
 <li class="img" v-for ="res in item.images" :key="res.id">
  
  <img class ="img2" :src="res" alt="Image" />

</li>
</div>
<button @click="deleteProduct" class="button1">Delete Product</button>
</ul>

</template>

<script>
import AddProduct from './components/AddProduct.vue'
import axios from 'axios';
export default {
  name:'App',

  components:{
    AddProduct,
  },

  data(){
    return{
    list:[]  
    }
  },

  async mounted(){
    let result=await axios.get("http://mail.zaxtom.com:3000/products");
    result.data.reverse();
    console.log("api data",result.data);
    this.list=result.data;
  }
};
</script>

<style>
.im {
  justify-content: center;
  border: 2px solid #ccc;
  border-color: black;
  width:"fit-content";
  list-style: none;
  display: flex; 
  flex-wrap: wrap;
  padding: 10px; 
  display: flex;
};
.img{
  
  margin-right: 10px;
  width:"fit-content";
  border: 1px solid #ccc;
  border-color: #de0e15;
  padding: 10px;
};
.red{
  text-align: center;
  font-size: 50px;
  font-family: Arial, Helvetica, sans-serif;
  text-decoration: #de0e15;
}
.lis {
  list-style-type: none; /* Remove default list styles */
  padding: 10px;
  border: 1px solid #ddd; /* Add a border for separation */
  margin-bottom: 10px; /* Add space between cart items */
background-color: hwb(60 98% 0%);
border-color: #de0e15;
border-width: 3px;
border-style: dashed;
}

.lis li {
  margin-bottom: 5px; /* Add space between list items */
}
.re{
  display:flex;
  font-family: Arial, Helvetica, sans-serif;
  background-color: hsl(68, 93%, 89%);
  padding-bottom: 1px;
  font-size:medium;
  font-size:20px;
  font-style: normal;
  

}


</style>