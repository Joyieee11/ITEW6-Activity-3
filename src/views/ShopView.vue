<template>
  <div class="shop">
    <button class="logout-btn" @click="logout">LOGOUT</button>
    <div class="left-panel">
      <ProductList :products="animeMerchandise" :addItem="addItem" />
    </div>
    <div class="right-panel">
      <ShoppingCart :items="cartItems" :removeItem="removeItem" :updateQuantity="updateQuantity" />
    </div>
  </div>
</template>

<script>
import ProductList from '@/components/ProductList.vue';
import ShoppingCart from '@/components/ShoppingCart.vue';

export default {
  name: 'ShopView',
  components: {
    ProductList,
    ShoppingCart
  },
  props: {
    isLogin: Boolean,
  },
  data() {
    return {
      animeMerchandise: [
        { name: 'Naruto Hoodie', price: 35 },
        { name: 'Attack on Titan Poster Set', price: 20 },
        { name: 'My Hero Academia Funko Pop Figure', price: 12 },
        { name: 'Sailor Moon Backpack', price: 25 },
        { name: 'Dragon Ball Z T-shirt', price: 18 },
        { name: 'Studio Ghibli Plush Toy (Totoro)', price: 30 },
        { name: 'One Piece Mug', price: 10 },
        { name: 'Pokémon Trading Cards Booster Pack', price: 5 },
        { name: 'Demon Slayer Keychain Set', price: 15 },
        { name: 'Fullmetal Alchemist Poster', price: 8 }
      ],
      cartItems: [],
    }
  },
  methods: {
    logout() {
      localStorage.removeItem('loginID')
      this.$router.push('/login')
    },
    addItem(item) {
      if (localStorage.getItem('loginID')) {
        const index = this.cartItems.findIndex(cartItem => cartItem.name === item.name);
        if (index !== -1) {
          this.cartItems[index].quantity++;
        } else {
          this.cartItems.push({ ...item, quantity: 1 });
        }
      } else {
        alert('LOGIN FIRST!');
        this.$router.push('/login');
      }
    },
    removeItem(index) {
      this.cartItems.splice(index, 1);
    },
    updateQuantity(index, newQuantity) {
      if (newQuantity < 1) {
        newQuantity = 1;
      }
      this.cartItems[index].quantity = parseInt(newQuantity);
    }
  }
}
</script>


<style scoped>
.shop {
  display: flex;
  position: relative;
}

.logout-btn {
  position: absolute;
  top: 10px;
  left: 10px;
  background-color: #ff0000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.logout-btn:hover {
  background-color: #f81414;
}

.left-panel {
  flex: 1;
  padding: 20px;
  background-color: #f4f4f4;
}

.right-panel {
  flex: 1;
  padding: 20px;
  background-color: #ffffff;
  border-left: 1px solid #dddddd;
}
</style>
