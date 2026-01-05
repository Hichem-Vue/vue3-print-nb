<script setup>
import { computed } from 'vue'

import product1 from '@/assets/products/1.jpg'
import product2 from '@/assets/products/2.jpg'
import product3 from '@/assets/products/3.jpg'
import product4 from '@/assets/products/4.jpg'

const products = [
  {
    id: 1,
    name: 'Product A',
    characteristics: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
    price: 19.99,
    qty: 5,
    image: product1,
  },
  {
    id: 2,
    name: 'Product B',
    characteristics: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
    price: 29.99,
    qty: 2,
    image: product2,
  },
  {
    id: 3,
    name: 'Product C',
    characteristics: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
    price: 9.99,
    qty: 10,
    image: product3,
  },
  {
    id: 4,
    name: 'Product D',
    characteristics: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
    price: 15.99,
    qty: 7,
    image: product4,
  },
  {
    id: 5,
    name: 'Product E',
    characteristics: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
    price: 12.99,
    qty: 18,
    image: product2,
  },
  {
    id: 6,
    name: 'Product F',
    characteristics: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
    price: 25.99,
    qty: 9,
    image: product3,
  },
]

const totalProducts = computed(() => products.length)

const totalQty = computed(() => products.reduce((sum, product) => sum + product.qty, 0))

const totalValue = computed(() =>
  products.reduce((sum, product) => sum + product.price * product.qty, 0),
)

const handlePrint = () => {}
</script>

<template>
  <div class="app">
    <header class="header">
      <h1>Products List</h1>
      <button class="print-button" type="button" @click="handlePrint">Print</button>
    </header>

    <table class="products-table">
      <thead>
        <tr>
          <th>Product Name</th>
          <th>Price</th>
          <th>Qty</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td>
            <div class="product-name">
              <img class="product-image" :src="product.image" :alt="product.name" />
              <ul>
                <li>{{ product.characteristics[0] }}</li>
                <li>{{ product.characteristics[1] }}</li>
                <li>{{ product.characteristics[2] }}</li>
                <li>{{ product.characteristics[3] }}</li>
                <li>{{ product.characteristics[4] }}</li>
              </ul>
            </div>
          </td>
          <td>{{ product.price }}</td>
          <td>{{ product.qty }}</td>
        </tr>
      </tbody>
    </table>

    <section class="stats-card">
      <h2>Summary</h2>
      <div class="stats-grid">
        <div class="stat">
          <div class="stat-label">Total Products</div>
          <div class="stat-value">{{ totalProducts }}</div>
        </div>
        <div class="stat">
          <div class="stat-label">Total Quantity</div>
          <div class="stat-value">{{ totalQty }}</div>
        </div>
        <div class="stat">
          <div class="stat-label">Total Value</div>
          <div class="stat-value">${{ totalValue.toFixed(2) }}</div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.app {
  max-width: 900px;
  margin: 40px auto;
  padding: 24px;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.12);
  font-family:
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    sans-serif;
}

.products-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 15px;
}

.products-table thead {
  background: #f1f5f9;
}

.products-table th,
.products-table td {
  padding: 10px 12px;
  text-align: left;
  border-bottom: 1px solid #e2e8f0;
}

.products-table th {
  font-weight: 600;
  color: #475569;
}

.products-table tbody tr:nth-child(even) {
  background-color: #f8fafc;
}

.products-table tbody tr:hover {
  background-color: #e0f2fe;
}

.product-name {
  display: flex;
  align-items: center;
  gap: 12px;
}

.product-image {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 12px;
}

.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 24px;
}

.header h1 {
  font-size: 26px;
  font-weight: 600;
  color: #0f172a;
  margin: 0;
}

.print-button {
  padding: 8px 16px;
  border-radius: 999px;
  border: none;
  background: #0ea5e9;
  color: #ffffff;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  box-shadow: 0 4px 10px rgba(14, 165, 233, 0.35);
  transition:
    transform 0.1s ease,
    box-shadow 0.1s ease,
    background-color 0.1s ease;
}

.print-button:hover {
  background: #0284c7;
  box-shadow: 0 6px 16px rgba(14, 165, 233, 0.45);
  transform: translateY(-1px);
}

.print-button:active {
  transform: translateY(0);
  box-shadow: 0 3px 8px rgba(15, 23, 42, 0.4);
}

.stats-card {
  margin-top: 40px;
  padding: 16px 20px;
  border-radius: 12px;
  border: 1px solid #e2e8f0;
  background: linear-gradient(135deg, #0ea5e9, #22c55e);
  color: #f9fafb;
  /* box-shadow: 0 5px 12px rgba(15, 23, 42, 0.35); */
}

.stats-card h2 {
  margin: 0 0 12px;
  font-size: 18px;
  font-weight: 600;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 16px;
}

.stat {
  padding: 10px 12px;
  border-radius: 10px;
  background-color: rgba(15, 23, 42, 0.2);
  backdrop-filter: blur(4px);
}

.stat-label {
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  opacity: 0.85;
}

.stat-value {
  margin-top: 4px;
  font-size: 18px;
  font-weight: 600;
}
</style>
