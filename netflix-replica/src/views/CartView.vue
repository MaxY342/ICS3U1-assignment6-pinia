<script setup>
import Topbar from '../components/Topbar.vue'
import Footer from '../components/Footer.vue'
import { useStore } from '../stores/index';

const store = useStore();
console.log(store);
</script>

<template>
    <Topbar />
    <div class="cart">
        <div class="content">
            <h1>Shopping Cart</h1>
            <div class="item-container">
                <div class="item" v-for="([key, value]) in store.cart">
                    <img :src="`https://image.tmdb.org/t/p/w500${value.url}`" />
                    <h1>{{ value.title }}</h1>
                    <div class="right-details">
                        <button @click="store.cart.delete(key)">Remove</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <Footer />
</template>

<style scoped>
.content {
    background-color: #151515;
    border-radius: 10px;
    color: white;
}

h1 {
  text-align: center;
  font-size: 2.5rem;
}

button {
  background-color: #e20c0c;
  color: white;
  padding: 1rem;
  border: 0;
  border-radius: 10px;
  transition: transform 0.2s;
}

button:hover {
  background-color: #c20000;
  cursor: pointer;
}

.right-details {
    display: flex;
    justify-content: flex-end;
}

.cart {
    display: flex;
    flex-direction: column;
    background-color: #2f2f2f;
    padding: 4rem;
    gap: 2rem;
}

.item-container {
    display: flex;
    flex-direction: column;
    gap: 5rem;
}

.item {
    display: grid;
    grid-template-columns: auto auto 1fr auto;
    gap: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
    align-items: center;
}

img {
    width: 30%;
    border-radius: 5%;
}
</style>