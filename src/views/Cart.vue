<template>
  <br>
  <div>
    
    <h1 class="mb-10 text-center text-2xl font-bold">Cart Items</h1>
    <div class="mx-auto max-w-5xl justify-center px-6 md:flex md:space-x-6 xl:px-0">
      <div class="rounded-lg md:w-2/3">
        <div v-for="cart in getCart" :key="cart.cart_id">
        <div class="justify-between mb-6 rounded-lg bg-white p-6 shadow-md sm:flex sm:justify-start">
          <img src="https://images.bisnis.com/posts/2023/03/12/1636532/3._kucing_anggora__ciri,_jenis,_cara_merawat,_dan_harganya_-_daily_paws.jpg" alt="product-image" class="w-full rounded-lg sm:w-40" />
          <div class="sm:ml-4 sm:flex sm:w-full sm:justify-between">
            <div class="mt-5 sm:mt-0">
              <h2 class="text-lg font-bold text-gray-900">{{ cart.name }}</h2>
              <p class="mt-1 text-xs text-gray-700">36EU - 4US</p>
            </div>
            <div class="mt-4 flex justify-between sm:space-y-6 sm:mt-0 sm:block sm:space-x-6">
              <div class="flex items-center border-gray-100">
                <span class="cursor-pointer rounded-l bg-gray-100 py-1 px-3.5 duration-100 hover:bg-blue-500 hover:text-blue-50"  @click="changeQty({cartId: cart.cart_id, typeQty: 'minus'})"> - </span>
                <input class="h-8 w-8 border bg-white text-center text-xs outline-none" type="" :value="cart.qty" min="1" />
                <span class="cursor-pointer rounded-r bg-gray-100 py-1 px-3 duration-100 hover:bg-blue-500 hover:text-blue-50" @click="changeQty({cartId: cart.cart_id, typeQty: 'plus'})"> + </span>
              </div>
              <div class="flex items-center space-x-4">
                <p class="text-sm">Rp. {{ cart.regular_price }}</p>

                <button type="button" @click="removeItem(cart.cart_id)">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24"
                          stroke="currentColor">
                          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
                        </svg>
              </button>

              </div>
            </div>
          </div>
        </div>
      </div>
      </div>
      <!-- Sub total -->
      <div class="mt-6 h-full rounded-lg border bg-white p-6 shadow-md md:mt-0 md:w-1/3">
        
        <div class="mb-2 flex justify-between">
          <p class="text-gray-700">Subtotal</p>
          <p class="text-gray-700">{{totalHarga()}}</p>
        </div>

        <hr class="my-4" />
        
        <div class="flex justify-between">
          <p class="text-lg font-bold">Total</p>
          <div class="">
            <p class="mb-1 text-lg font-bold">{{totalHarga() }}</p>
           
          </div>
        </div>
        <router-link to="/checkout">
        <button class="mt-6 w-full rounded-md bg-blue-500 py-1.5 font-medium text-blue-50 hover:bg-blue-600">Check out</button>
    </router-link>

      </div>
    </div>

  </div>

</template>
<script>
import { mapGetters, mapActions } from 'vuex';

export default {

    computed: {
        ...mapGetters('cart', ['getCart']),
       
    },

    methods: {
        ...mapActions('cart', ['fetchCart']),
        ...mapActions('product', ['fetchProduk']),
        // ...mapActions('produk', ['addToCart']),
   
        totalHarga() {
          this.total = this.getCart.reduce((acc, produk) => {
            return acc + parseFloat(produk.regular_price * produk.qty);
          }, 0);
          return this.total.toFixed(1);
        },
    // remove cart
    removeItem(cartId) {
      this.$store.dispatch('cart/removeFromCart', cartId);
    },  
    changeQty(cartId, typeQty) {
      this.$store.dispatch('cart/changeQuantity', cartId,typeQty);
    },  
  },
  
    beforeMount() {
      this.fetchProduk();
      this.fetchCart();
    },
    mounted() {
        this.fetchCart();
    }
}
</script>