<template>
  <div class="bg-white">
    <div
      class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-20 lg:max-w-7xl lg:px-8"
    >
      <h2 class="text-2xl font-bold tracking-tight text-gray-900">
        Fake Store Api
      </h2>

      <div
        class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8"
      >
        <div
          v-for="product in products"
          :key="product.id"
          class="group relative border p-2 shadow-[rgba(13,_38,_76,_0.19)_0px_9px_20px] rounded-xl"
        >
          <div
            class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-md bg-gray-200 lg:aspect-none group-hover:opacity-75 lg:h-80"
          >
            <img
              :src="product.image"
              class="h-full w-full object-cover object-center lg:h-full lg:w-full"
            />
          </div>
          <div class="mt-4 flex gap-2 flex-col">
            <p class="mt-1 text-sm font-bold uppercase">
              {{ product.category }}
            </p>
            <h2 class="text-sm text-gray-700">
              {{ product.title }}
            </h2>
            <p
              class="text-sm font-bold text-center align-bottom py-2 bg-[#C68484] text-[#EEEEEE] rounded-full"
            >
              {{ product.price }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
    };
  },
  async mounted() {
    await this.getProducts();
  },
  methods: {
    async getProducts() {
      try {
        const response = await fetch("https://fakestoreapi.com/products");
        const data = await response.json();

        this.products = data;

        console.log(data);
      } catch (error) {
        console.error("Error fetching products: ", error);
      }
    },
  },
};
</script>
