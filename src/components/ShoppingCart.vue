<!-- ShoppingCart.vue -->
<template>
  <div class="shopping-cart">
    <h2 class="title-cart">Shopping Cart</h2>
    
    <h2 class="cart-total">Total: ${{ total }}</h2>
    <table>
      <thead>
        <tr>
          <th>Item</th>
          <th>Quantity</th>
          <th>Price</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in items" :key="index" class="cart-item">
          <td>{{ item.name }}</td>
          <td>
            <input type="number" v-model="item.quantity" min="1" @input="updateQuantity(index, $event.target.value)">
          </td>
          <td>${{ item.price * item.quantity }}</td>
          <td><button @click="removeItem(index)" class="remove-btn">Remove</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'ShoppingCart',
  props: {
    items: Array,
    removeItem: Function,
    updateQuantity: Function
  },
  computed: {
    total() {
      return this.items.reduce((total, item) => total + (item.price * item.quantity), 0);
    }
  }
}
</script>

<style scoped>
.shopping-cart {
  margin-top: 20px;
}

.title-cart {
  font-size: 24px;
  color: #ff0000;
  float: left;
}

.cart-total {
  font-size: 24px;
  color: #ff0000;
  float: right;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #dddddd;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #ff0000; 
  color: #ffffff; 
}

.cart-item input[type="number"] {
  width: 50px;
}

.remove-btn {
  background-color: #000000; 
  color: #ffffff;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
