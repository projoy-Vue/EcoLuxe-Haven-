<template>
  <div class="product-highlights">
    <h1>Our Best Picks for You</h1>
    <div class="carousel">
      <!-- Product Card Carousel -->
      <div class="product-card" v-for="product in products" :key="product.id">
        <!-- Product Image with Zoom/Flip Effect -->
        <div class="product-image" @mouseenter="hoverProduct(product)" @mouseleave="unhoverProduct(product)">
          <img :src="product.image" :alt="product.name" />
          <!-- Quick View Button -->
          <button class="quick-view" @click="openQuickView(product)">Quick View</button>
        </div>
        <!-- Product Info -->
        <div class="product-info">
          <h3>{{ product.name }}</h3>
          <p class="price">${{ product.price }}</p>
          <!-- Ratings and Reviews -->
          <div class="ratings">
            <i v-for="n in product.rating" class="fas fa-star" :key="n"></i>
            <span>({{ product.reviews }} reviews)</span>
          </div>
          <!-- Add to Cart Button -->
          <button class="add-to-cart" @click="addToCart(product)">Add to Cart</button>
        </div>
      </div>
    </div>
    <!-- Quick View Modal -->
    <modal v-if="showQuickView" @close="showQuickView = false">
      <div class="quick-view-content">
        <img :src="selectedProduct.image" :alt="selectedProduct.name" />
        <h3>{{ selectedProduct.name }}</h3>
        <p>{{ selectedProduct.description }}</p>
        <button @click="addToCart(selectedProduct)" class="add-to-cart-btn">Add to Cart</button>
        <button @click="showQuickView = false" class="close-quick-view">Close</button>
      </div>
    </modal>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        { id: 1, name: "Eco-Friendly Tumbler", price: 20, rating: 4, reviews: 25, image: "https://picsum.photos/536/354" },
        { id: 2, name: "Reusable Bamboo Straws", price: 15, rating: 5, reviews: 40, image: "https://picsum.photos/536/354" },
        { id: 3, name: "Organic Cotton Towel", price: 25, rating: 3, reviews: 15, image: "https://picsum.photos/536/354" },
        { id: 4, name: "Reusable Bamboo Straws", price: 15, rating: 5, reviews: 40, image: "https://picsum.photos/536/354" },
        { id: 5, name: "Organic Cotton Towel", price: 25, rating: 3, reviews: 15, image: "https://picsum.photos/536/354" },
        { id: 6, name: "Organic Cotton Towel", price: 25, rating: 3, reviews: 15, image: "https://picsum.photos/536/354" },
        { id: 7, name: "Organic Cotton Towel", price: 25, rating: 3, reviews: 15, image: "https://picsum.photos/536/354" },
        { id: 8, name: "Organic Cotton Towel", price: 25, rating: 3, reviews: 15, image: "https://picsum.photos/536/354" },
        // Add more products here
      ],
      showQuickView: false,
      selectedProduct: '',
    };
  },
  methods: {
    hoverProduct(product) {
      // Optional hover interaction logic
    },
    unhoverProduct(product) {
      // Optional hover interaction logic
    },
    openQuickView(product) {
      this.selectedProduct = product;
      this.showQuickView = true;
    },
    addToCart(product) {
      // Logic for adding product to cart
    },
  },
};
</script>

<style scoped>
/* Product Carousel and Cards */
.product-highlights {
  position: relative;
  /* background-color: #f5f5f5; */
  padding: 2rem;
  background: linear-gradient( to right, #57d87e,  #282c35  );
}

h1 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.5rem;
  font-weight: bold;
}

.carousel {
 display: grid;
 grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
 grid-gap: 20px;
}

.product-card {
  background: white;
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  width: 300px;
  transition: transform 0.3s;
}

.product-card:hover {
  transform: scale(1.05);
}

.product-image {
  position: relative;
  overflow: hidden;
}

.product-image img {
  width: 100%;
  transition: transform 0.3s;
}

.product-image:hover img {
  transform: scale(1.1);
  /* Zoom effect */
}

.quick-view {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  background-color: black;
  color: white;
  ;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  opacity: 0;
  transition: opacity 0.3s;
}

.product-image:hover .quick-view {
  opacity: 1;
}

.product-info {
  padding: 15px;
  text-align: center;
}

.ratings i {
  color: #fbc02d;
  /* Gold for stars */
}

.add-to-cart {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
}

.add-to-cart:hover {
  background-color: #218838;
}

/* Quick View Modal */
.quick-view-content {
  text-align: center;
  padding: 20px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 500px;
  z-index: 999;
 
}

.quick-view-content img {
  max-width: 100%;
  margin-bottom: 15px;
}

.quick-view-content h3 {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 10px;
}
.add-to-cart-btn {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
}
.add-to-cart-btn:hover {
  background-color: #218838;
}
.close-quick-view {
  background-color: black;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
}

.close-quick-view:hover {
  background-color: #212529;
}

/* Responsive Styles */
@media (max-width: 768px) {
  .carousel {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }

  .product-card {
    width: 100%;
  }
}
</style>