<template>
  <li class="product">
    <div class="product__data">
      <div class="product__image">
        <img :src="image" :alt="title" />
      </div>
      <div class="product__text">
        <h3>{{ title }}</h3>
        <p>{{ description }}</p>
        <h4 class="product__price">R{{ price }}</h4>
      </div>
      <div class="product__actions">
        <button @click="addToCart">Add to Cart</button>
      </div>
    </div>
  </li>
</template>

<script>
import { mapActions } from 'vuex';

export default {
  props: ['id', 'image', 'title', 'price', 'description'],
  methods: {
    ...mapActions('cart', ['addProductToCart']),
    addToCart() {
      this.addProductToCart({
        id: this.id,
        image: this.image,
        title: this.title,
        price: this.price
      });
    }
  }
};
</script>

<style scoped>
li {
  margin: 1.5rem auto;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  border-radius: 1rem;
}

.product__data {
  display: grid;
  /* grid-template-columns: 1fr 2fr 1fr; */
  justify-content: center;
}

.product__image {
  text-align: center;
}

.product__image img {
  height: 10rem;
  width: 10rem;
  object-fit: cover;
  border-radius: 50%;
  margin: 2rem;
}

.product__price {
  text-transform: capitalize;
  font-weight: var(--fw-200);
}

.product__actions {
  align-self: end;
  justify-self: end;
}

button {
  font: inherit;
  cursor: pointer;
  background-color: var(--clr-neutral-200);
  color: var(--clr-primary-900);
  border: 1px solid var(--clr-primary-500);
  padding: 0.5rem 1.5rem;
  border-radius: 30px;
}

button:hover,
button:active {
  background-color: var(--clr-primary-900);
  border-color: var(--clr-primary-900);
  color: var(--clr-neutral-100);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
}
</style>
