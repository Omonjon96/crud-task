<template>
  <div class="hello">
    <div class="container">
      <div class="row">
        <div class="col">
            <form>
                <div class="form-group">
                  <label for="exampleInputEmail1">Product Name</label>
                  <input 
                    type="text" 
                    class="form-control" 
                    id="exampleInputEmail1" 
                    aria-describedby="emailHelp" 
                    placeholder="Enter product"
                    :value="product.name"
                    @input="product.name = $event.target.value"
                  >
                </div>
                <div class="form-group">
                  <label for="exampleInputPassword1">Quantity</label>
                  <input 
                    type="number" 
                    class="form-control" 
                    id="exampleInputPassword1" 
                    placeholder="Quantity"
                    :value="product.quantity"
                    @input="product.quantity = $event.target.value"
                  >
                </div>
                <div class="form-group">
                  <label for="exampleInputPassword1">Price</label>
                  <input 
                    type="number" 
                    class="form-control" 
                    id="exampleInputPrice" 
                    placeholder="Price"
                    :value="product.price"
                    @input="product.price = $event.target.value"
                  >
                </div>

                <div class="form-group">
                  <label for="exampleFormControlTextarea1">Description</label>
                  <textarea 
                    class="form-control" 
                    id="exampleFormControlTextarea1" 
                    rows="3"
                    :value="product.description"
                    @input="product.description = $event.target.value"
                  >
                  </textarea>
                </div>
                 <div class="form-group">
                    <label for="exampleFormControlSelect1">Options</label>
                    <select 
                      class="form-control" 
                      id="exampleFormControlSelect1"
                      v-model="selectedOption"
                    >
                      <option v-for="option in options">{{ option }}</option>
                    </select>
                </div>
                <div class="switch">
                      <app-switch v-model="dataSwitch"></app-switch>
                </div>
                <button 
                  type="submit" 
                  class="btn btn-primary"
                  @click.prevent="submitted"  
                >
                  Submit</button>
            </form>
        </div>
        <div class="col center-column" v-if="isSubmitted">
          <h5 class="center-column-heading">Show spended expenses and datas</h5>
          <p>Product Name: {{ product.name }} </p>
          <p>Quantity: {{ product.quantity }}</p>
          <p>Price: {{ product.price }}</p>
          <p>Description: {{ product.description }} </p>
          <p>Option: </p>
          <p>Switched: {{ dataSwitch }}</p>
        </div>
        <div class="col">
            <h5>Deatiled Info about User account</h5>
            <label for="Balance"> Balance: {{ balance }} $ </label>
        </div>
      </div>
    </div>
   
    
    
  </div>
</template>

<script>
import Switch from '@/components/Switch.vue'
export default {
  name: 'HelloWorld',
  data(){
    return{
    product: [
      {
        name: '',
        quantity: 0,
        price: 0,
        description:''
      }
    ],
    balance: 1500,
    selectedOption:'E-category',
    options:['A-category', 'B-category', 'C-category', 'D-category', 'E-category'],
    dataSwitch: true,
    isSubmitted: false
    }
  },
  components:{
    appSwitch: Switch
  },
  methods: {
    submitted(){
      this.isSubmitted = true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .center-column-heading{
    text-align: center;
  }

  .center-column{
    text-align: left;
  }
</style>
