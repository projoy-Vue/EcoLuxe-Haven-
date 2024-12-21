# ecommerce-landing

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

```sh
    <section class="featured-products">
      <!-- Section Title -->
      <h2 class="section-title">Our Best Picks for You</h2>
  
      <!-- Sorting and Filtering Options -->
      <div class="sorting-filtering">
        <select v-model="sortOption" @change="sortProducts">
          <option value="popularity">Sort by Popularity</option>
          <option value="price-asc">Sort by Price: Low to High</option>
          <option value="price-desc">Sort by Price: High to Low</option>
        </select>
  
        <select v-model="categoryFilter" @change="filterProducts">
          <option value="all">All Categories</option>
          <option v-for="category in categories" :key="category">{{ category }}</option>
        </select>
      </div>
  
      <!-- Product Grid Layout -->
      <div class="product-grid">
        <div 
          v-for="product in filteredProducts" 
          :key="product.id" 
          class="product-card" 
          @click="openQuickView(product)"
        >
          <img :src="product.image" :alt="product.title" class="product-image" />
          <div class="product-info">
            <h3 class="product-name">{{ product.title }}</h3>
            <p class="product-price">{{ product.price | currency }}</p>
          </div>
          <button class="quick-view-btn">Quick View</button>
        </div>
      </div>
  
      <!-- Quick View Modal -->
      <div v-if="showQuickView" class="quick-view-modal">
        <div class="modal-content">
          <button class="close-modal" @click="closeQuickView">&times;</button>
          <img :src="selectedProduct.image" :alt="selectedProduct.title" />
          <div class="modal-info">
            <h3>{{ selectedProduct.title }}</h3>
            <p>{{ selectedProduct.description }}</p>
            <p>{{ selectedProduct.price | currency }}</p>
            <button class="add-to-cart-btn">Add to Cart</button>
          </div>
        </div>
      </div>
    </section>  
  <script>
   import axios from 'axios';
  
  export default {
    data() {
      return {
        products: [],
        sortOption: 'popularity',
        categoryFilter: 'all',
        showQuickView: false,
        selectedProduct: {},
        filteredProducts: [],
        categories: [],
      };
    },
    methods: {
      async fetchProducts() {
        try {
          const response = await axios.get('https://fakestoreapi.com/products');
          this.products = response.data;
          this.filteredProducts = this.products; // Initialize filtered products
          this.extractCategories(); // Extract categories from the fetched products
        }, catch (error) {
          console.error('Error fetching product data:', error);
        }
      },
      extractCategories() {
        const allCategories = new Set(this.products.map(product => product.category));
        this.categories = Array.from(allCategories);
      },
      sortProducts() {
        if (this.sortOption === 'price-asc') {
          this.filteredProducts.sort((a, b) => a.price - b.price);
        } else if (this.sortOption === 'price-desc') {
          this.filteredProducts.sort((a, b) => b.price - a.price);
        }
      },
      filterProducts() {
        if (this.categoryFilter === 'all') {
          this.filteredProducts = this.products;
        } else {
          this.filteredProducts = this.products.filter(product => product.category === this.categoryFilter);
        }
      },
      openQuickView(product) {
        this.selectedProduct = product;
        this.showQuickView = true;
      },
      closeQuickView() {
        this.showQuickView = false;
      }
    },
    mounted() {
      this.fetchProducts(); // Fetch products on component mount
    },
    filters: {
      currency(value) {
        return `$${parseFloat(value).toFixed(2)}`;
      }
    }
  };
  </script>
  
  <style scoped>
  /* Your styles remain the same as before */
  </style>
```

cd ecommerce-landing