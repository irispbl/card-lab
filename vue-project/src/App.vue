<script>
import ITEMS from "./items.json";
export default {
  data() {
    return {
      items: ITEMS,
      title: "My Ecommerce",
      button: "Confirmar compra",
    };
  },
  computed: {
    showItems() {
      return this.items.slice(0, 5);
    },
    sumOfTotal() {
      for (let i = 0; i < this.items.length; i++) return;
    },
    yourTotalQuantityIs() {
      let counter = 0;
      for (let i = 0; i < this.items.length; i++) {
        counter += this.items[i].quantity;
      }
      return counter;
    },
    subTotal() {
      let counter = 0;
      for (let i = 0; i < this.items.length; i++) {
        counter += this.items[i].quantity * this.items[i].price;
      }
      return counter;
    },
  },
};
</script>

<template>
  <div>
    <h1 class="text-6xl font-bold mb-10">{{ title }}</h1>
  </div>
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Image</th>
        <th>Quantity</th>
        <th>Price</th>
        <th>Total</th>
      </tr>
    </thead>
    <tbody v-for="item of showItems" :key="item.uuid">
      <tr>
        <td>{{ item.name }}</td>
        <td><img class="w-24" :src="item.image" :alt="images" /></td>
        <td><input type="number" v-model="item.quantity" /></td>
        <td>{{ item.price }}</td>
        <td>{{ item.quantity * item.price }}</td>
      </tr>
    </tbody>
  </table>
  <div>{{ yourTotalQuantityIs }} articulos tiene tú carrito</div>
  <div class="text-center font-bold">
    El subtotal es de {{ subTotal }} euros
  </div>
  <button class="cursor-pointer p-2 bg-yellow-500">{{ button }}</button>
</template>
<style></style>
