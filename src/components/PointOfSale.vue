<template >
  <div class="hello">
    <button
      v-for="(item, index) of inventory"
      v-on:click="addToCheck(item)"
    >
      <img v-bind:src="getImage(item.image)" height="64">
      {{item.name}}
      ${{convertPrice(item.cost)}}

    </button>
    <p>
      <ul><u>Current Order</u> 
        <li v-for="(item, index) of theOrder"
        >{{item.name }} ${{convertPrice(item.cost)}}
        <button v-on:click="removeFromCheck(index, item.cost)">x</button>
        </li>
      </ul>
      <ul>subTotal ${{convertPrice(orderTotal)}}</ul>
      <ul>Tax 8% = ${{getTax(orderTotal)}}</ul>
      <ul>Total  ${{getTotal(orderTotal)}}</ul>
    </p>
    <button v-on:click="deleteAll">Resest</button>
  </div>
  


</template>

<script>
import inventory from '@/assets/inventory'

export default {
  name: 'hello',
  data () {
    return {
      inventory: inventory,
      msg: 'Welcome to Your Vue.js App',
      theOrder: [],
      orderTotal: 0
    }
  },
  // props: ['inventory'],
  methods: {
    getImage: function (x) {
      var strT = './static/' + x
      return strT
    },
    convertPrice: function (x) {
      var price = (x / 100).toFixed(2)
      return price
    },
    getTax: function (x) {
      var tax = (x * 0.0008).toFixed(2)
      return tax
    },
    getTotal: function (x) {
      var total = ((x + (x * 0.08)) / 100).toFixed(2)
      return total
    },
    addToCheck: function (item) {
      this.orderTotal = this.orderTotal + item.cost
      this.theOrder.push(item)
    },
    removeFromCheck: function (index, price) {
      this.theOrder.splice(index, 1)
      this.orderTotal = this.orderTotal - price
    },
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
