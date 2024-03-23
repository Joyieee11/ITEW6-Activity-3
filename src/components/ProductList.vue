<template>
  <div class="product-list">
    <h2 class="title">Anime Merch</h2>
    <ul>
      <li v-for="(product, index) in products" :key="index" class="product-item">
        <span class="product-name">{{ product.name }}</span> 
        <span class="product-price">${{ product.price }}</span>
        <button @click="addItem(product)" class="add-to-cart-btn">Add to Cart</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    products: Array,
    addItem: Function
  }
}
</script>

<style scoped>
.product-list {
  padding: 20px;
  background-color: #000000; 
}

.title {
  font-size: 24px;
  color: #ff0000;
  text-align: left;
}

.product-item {
  list-style: none;
  border-bottom: 1px solid #dddddd;
  padding: 10px 0;
  display: flex;
  align-items: center;
}

.product-name {
  flex: 2;
  color: #ffffff; 
  text-align: left
}

.product-price {
  flex: 1;
  color: #ffffff;
}

.add-to-cart-btn {
  background-color: #ff0000; 
  color: #ffffff; 
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
