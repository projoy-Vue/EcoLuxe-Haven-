<template>
    <div class="categories-section">
      <h2 class="section-title">Shop by Category</h2>
      <div class="category-grid">
        <div class="category-card" v-for="category in categories" :key="category.id">
          <!-- Lazy-loaded Image -->
          <img 
            :src="category.image" 
            :alt="category.name" 
            class="category-image"
            loading="lazy"
          />
          <div class="category-content">
            <h3>{{ category.name }}</h3>
            <p class="category-description">{{ category.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        categories: [
          {
            id: 1,
            name: "Eco-friendly Apparel",
            description: "Discover sustainable fashion.",
            image: "https://picsum.photos/536/354.jpg",
          },
          {
            id: 2,
            name: "Reusable Home Goods",
            description: "Explore eco-conscious products for your home.",
            image: "https://picsum.photos/536/354.jpg",
          },
          {
            id: 3,
            name: "Sustainable Tech",
            description: "Innovative technology that’s eco-friendly.",
            image: "https://picsum.photos/536/354.jpg",
          },
          // Add more categories here
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  /* Categories Section */
  .categories-section {
    background: linear-gradient(to right, #5f90cc, #161a20);
    padding: 2rem;
  }
  
  .section-title {
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2.5rem;
    font-weight: bold;
  }
  
  .category-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
  }
  
  .category-card {
    position: relative;
    overflow: hidden;
    border-radius: 15px;
    cursor: pointer;
    background-color: #fff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s, box-shadow 0.3s;
  }
  
  .category-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  }
  
  .category-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
    transition: transform 0.3s;
  }
  
  .category-card:hover .category-image {
    transform: scale(1.1); /* Zoom on hover */
  }
  
  .category-content {
    padding: 1.5rem;
    text-align: center;
  }
  
  .category-content h3 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
    color: #333;
  }
  
  .category-content .category-description {
    font-size: 1rem;
    color: #666;
  }
  
  /* Responsive Design */
  @media (max-width: 768px) {
    .category-grid {
      grid-template-columns: 1fr;
    }
  
    .category-card {
      height: auto;
      padding: 1rem;
    }
  
    .category-image {
      height: 150px;
    }
  
    .category-content h3 {
      font-size: 1.3rem;
    }
  
    .category-content .category-description {
      font-size: 0.9rem;
    }
  }
  </style>
  