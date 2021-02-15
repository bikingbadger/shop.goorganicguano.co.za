<template>
  <main>
    <the-header></the-header>
    <router-view></router-view>
  </main>
</template>

<script>
import TheHeader from './components/nav/TheHeader.vue';
export default {
  components: {
    TheHeader
  },
  methods: {
    addProductToCart(productData) {
      const productInCartIndex = this.cart.items.findIndex(
        ci => ci.productId === productData.id
      );

      if (productInCartIndex >= 0) {
        this.cart.items[productInCartIndex].qty++;
      } else {
        const newItem = {
          productId: productData.id,
          title: productData.title,
          image: productData.image,
          price: productData.price,
          qty: 1
        };
        this.cart.items.push(newItem);
      }
      this.cart.qty++;
      this.cart.total += productData.price;
    },

    removeProductFromCart(prodId) {
      const productInCartIndex = this.cart.items.findIndex(
        cartItem => cartItem.productId === prodId
      );
      const prodData = this.cart.items[productInCartIndex];
      this.cart.items.splice(productInCartIndex, 1);
      this.cart.qty -= prodData.qty;
      this.cart.total -= prodData.price * prodData.qty;
    },
    login() {
      this.isLoggedIn = true;
    },
    logout() {
      this.isLoggedIn = false;
    }
  }
};
</script>

<style>
:root {
  --ff-sans: 'IBM Plex Sans', sans-serif;
  --ff-serif: 'IBM Plex Serif', serif;

  /* small screen font-sizes */
  --fs-200: 0.75rem;
  --fs-300: 1rem;
  --fs-400: 1.25rem;
  --fs-500: 1.375rem;
  --fs-600: 1.75rem;
  --fs-900: 2.125rem;

  --fw-200: 200;
  --fw-300: 300;
  --fw-400: 400;
  --fw-700: 700;

  --clr-neutral-100: #fff;
  --clr-neutral-200: #eef1f6;
  --clr-neutral-300: #a9afbc;
  --clr-neutral-400: #737b8c;
  --clr-neutral-500: #434956;
  --clr-neutral-900: #020203;

  --clr-primary-300: hsl(143, 46%, 19%, 0.3);
  --clr-primary-400: hsl(143, 46%, 19%, 0.5);
  --clr-primary-500: hsl(143, 46%, 19%, 0.7);
  --clr-primary-900: hsl(143, 46%, 19%, 1);

  --clr-accent-300: hsla(22, 73%, 51%, 0.3);
  --clr-accent-400: hsla(22, 73%, 51%, 0.5);
  --clr-accent-500: hsla(22, 73%, 51%, 0.7);
  --clr-accent-900: hsla(22, 73%, 51%, 1);

  --br: 1rem;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 66%;
  margin: 0 auto;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
