<template> 
  <MainComponent msg="This is Vue main app" :product="product" :loading="loading"/>
</template>

<script>
import MainComponent from "./components/main-component.vue";
const api =  require("@home/api");

export default {
  id: "app",
  name: "App",
  components: {
    MainComponent,
  },
  data() {
    return {
      loading: false,
      product: null,
      error: null,
    }
  },
  created() {
    // watch the params of the route to fetch the data again
    this.$watch(
      () => this.$route,
      () => {
        this.fetchProduct()
      },
      // fetch the data when the view is created and the data is
      // already being observed
      { immediate: true }
    )
  },
  methods: {
    fetchProduct() {
      this.error = this.post = null
      this.loading = true

      const searchParams = new URLSearchParams(window.location.search);

      api.fetchProduct({ id: searchParams.get('productId') })
        .then((res) => {
          this.product = res;
          this.loading = false;
        })
        .catch(() => {
          this.loading = false;
        });
    },
  },
};
</script>

<style>
  #app {
    margin-top: 60px;
  }
</style>
