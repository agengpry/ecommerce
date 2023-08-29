<template>
  <div class="relative flex min-h-screen flex-col justify-center overflow-hidden bg-gray-50 py-12">
    <div class="relative bg-white px-6 pt-10 pb-9 shadow-xl mx-auto w-full max-height-10 rounded-2xl ">
      <div class="mx-auto flex w-full max-w-md flex-col space-y-16">
        <div class="flex flex-col items-center justify-center text-center space-y-2">
          <h2 class="mt-6 text-3xl font-bold">

          </h2>
        </div>

        <div>
          <form>

            <div class="flex flex-col items-center space-y-2">

              <svg xmlns="http://www.w3.org/2000/svg" class="text-green-600 w-28 h-28 mb-10" fill="none"
                viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>

              <div class="flex flex-col space-y-1">

                <h1 class="text-4xl font-bold text-center">Sukses!</h1>
                <p class="font-bold">Terimakasih untuk pembeliannya!</p>
              </div>
            </div>
          </form>
        </div>
      </div>

      <div class="pt-20 ">
        <div class="container mx-auto px-4">
          <div class="message text-center">
            <h1 class="text-3xl font-bold pt-10">Struck</h1>
          </div>
          <div class="mx-10 mt-10 ">
            <div class="grid grid-cols-2" style="margin-left: 10%;">
              <div>
                <dl
                  class="max-w-md text-gray-900 divide-y divide-gray-200 dark:text-white dark:divide-gray-700 text-center">
                  <div class="flex flex-col pb-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Nama Pemesan :
                    </dt>
                    <dd class="text-lg font-semibold">{{ getOrder.user.name }}</dd>
                  </div>
                  <div class="flex flex-col pb-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Kode Pemesanan :
                    </dt>
                    <dd class="text-lg font-semibold">{{ getOrder.code }}</dd>
                  </div>
                  <div class="flex flex-col pb-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Alamat Email :
                    </dt>
                    <dd class="text-lg font-semibold">{{ getOrder.user.email }}</dd>
                  </div>
                  <div class="flex flex-col py-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Alamat Rumah :
                    </dt>
                    <dd class="text-lg font-semibold">
                      {{ getOrder.shipping_address.address }}, {{ getOrder.shipping_address.city }}, {{
                        getOrder.shipping_address.state }}, {{ getOrder.shipping_address.country }}, {{
    getOrder.shipping_address.postal_code }}
                    </dd>
                  </div>
                  <div class="flex flex-col pt-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Nomor Telpon :
                    </dt>
                    <dd class="text-lg font-semibold">
                      {{ getOrder.shipping_address.phone }}
                    </dd>
                  </div>
                </dl>
              </div>
              <div>
                <dl
                  class="max-w-md text-gray-900 divide-y divide-gray-200 dark:text-white dark:divide-gray-700 text-center">
                  <div class="flex flex-col pb-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Metode Pembayaran :
                    </dt>
                    <dd class="text-lg font-semibold">{{ getOrder.orders[0].payment_type }}</dd>
                  </div>
                  <div class="flex flex-col pb-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Metode Pengiriman :
                    </dt>
                    <dd class="text-lg font-semibold">{{ getOrder.orders[0].delivery_type }}</dd>
                  </div>
                  <div class="flex flex-col py-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Alamat Tagihan :
                    </dt>
                    <dd class="text-lg font-semibold">
                      {{ getOrder.shipping_address.address }}, {{ getOrder.shipping_address.city }}, {{
                        getOrder.shipping_address.state }}, {{ getOrder.shipping_address.country }}, {{
    getOrder.shipping_address.postal_code }}
                    </dd>
                  </div>
                  <div class="flex flex-col pt-3">
                    <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                      Total Harga Barang :
                    </dt>
                    <dd class="text-lg font-semibold">
                      {{ getOrder.orders[0].grand_total }}
                    </dd>
                  </div>
                </dl>
              </div>
            </div>
          </div>
          {{ orderData }}
        </div>
      </div>
    </div>
  </div>
</template>
    
<script>
import { mapGetters } from 'vuex';
export default {
  props: ['orderCode'],
  computed: {
    ...mapGetters('order', ['getOrder']),
  },
  created() {
    this.$store.dispatch('order/fetchOrderData', this.orderCode);
  },
};
</script>