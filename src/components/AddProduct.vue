<template>
    <h1 style="text-align: center; border:3px; background-color:hwb(69 25% 2%); border: 1px solid #ccc;
    border-color: hsl(0, 94%, 51%);border-width:3px
    ">ADD BLOG</h1>
    <div class="fr">
    <form class="red">
      <label ></label>
      <input type="text" name="product" v-model="title"/>
      <br/>
    
      <label >Price        </label>
      <input type="text" name="price" v-model="price"/>
      <br/>
      <label >Description</label>
      <input type="text" name="description" v-model="description"/>
      <br/>
      <label>Brand</label>
      <input type="text" name="brand" v-model="brand"/>
      <br/>
      
      <button v-on:click="addUser()" class="green">Add User</button>
    </form>
</div>
    </template>

    <script>
    import axios from 'axios'
export default{
      name:'AddProduct',
      data(){
        return{
          title:'',
          price:'',
          description:'',
          brand:'',
        }
      },
      methods:{
        async addUser(){
          let result = await axios.post("http://mail.zaxtom.com:3000/products",{
            title:this.title,
            price:this.price,
            description:this.description,
            brand:this.brand,
          });
          console.log(result.data);
        },
       
    }
}
</script>

<style>

.red{
    align-content: center;
    background-color: rgb(198, 234, 252);
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 300px; /* Adjust the width as needed */
  } 
  button{
    justify-content: center;
    margin: 10px;
    padding: 10px;
    background-color: hwb(249 2% 51%);
    color: white;
    border-radius: 5px;
    border: none;
    align-content: center;
    
  } 
  label {
    
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  input {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    box-sizing: border-box;
  }
  .fr{
    justify-content: center;
margin-left: 580px;
  }
  .green{
    margin-left: 105px;
  }
</style>