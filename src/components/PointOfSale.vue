<template >
  <div class="hello">
<!-- loop to set up series of buttons for each item. set function to execute on click to add item to check-->

    <button
      v-for="(item, index) of inventory"
      v-on:click="addToCheck(item)"
    >

<!--     bring in image associated with each item. run convert price function to get correct format -->
      <img v-bind:src="getImage(item.image)" height="64">
      {{item.name}}
      ${{convertPrice(item.cost)}}
    </button>


    <p>
      <ul><u>Current Order</u> 
<!--       loop to list out all selected items. run convert for correct format -->
        <li v-for="(item, index) of theOrder"
        >{{item.name }} ${{convertPrice(item.cost)}}
        <!-- set up buttons to delete items. set function to execute  -->
        <button v-on:click="removeFromCheck(index, item.cost)">x</button>
        </li>
      </ul>
<!--       display computed amounts with seperate functions for each coputation -->
      <ul>subTotal ${{convertPrice(orderTotal)}}</ul>
      <ul>Tax 8% = ${{getTax(orderTotal)}}</ul>
      <ul>Total  ${{getTotal(orderTotal)}}</ul>
    </p>
    <!-- set up buttons to delete all -->
    <button v-on:click="deleteAll">Resest</button>
  </div>
  


</template>

<script>
//bring in the objects for all items
import inventory from '@/assets/inventory'

export default {
  name: 'hello',
//define variables to be accessed by this reference
  data () {
    return {
      inventory: inventory,
      msg: 'Welcome to Your Vue.js App',
      theOrder: [],
      orderTotal: 0
    }
  },


  methods: {
//easier to set up string to access image with a function
    getImage: function (x) {
      var strT = './static/' + x
      return strT
    },

      // functions to compute amounts
      // convert price in cents to dollars
    convertPrice: function (x) {
      var price = (x / 100).toFixed(2)
      return price
    },
    //compute tax at 8%
    getTax: function (x) {
      var tax = (x * 0.0008).toFixed(2)
      return tax
    },
    //add up tax and total.  In this case, easier to just compute from 1 variable rather than adding other function results
    getTotal: function (x) {
      var total = ((x + (x * 0.08)) / 100).toFixed(2)
      return total
    },

    //functions to set items on check
    //push new items onto order
    addToCheck: function (item) {
      this.orderTotal = this.orderTotal + item.cost. //this references for variables defined in data
      this.theOrder.push(item)
    },

    //splice out removed item
    removeFromCheck: function (index, price) {
      this.theOrder.splice(index, 1)
      this.orderTotal = this.orderTotal - price
    },
    //reset array to empty and total to 0
    deleteAll: function () {
      this.theOrder = []
      this.orderTotal = 0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
