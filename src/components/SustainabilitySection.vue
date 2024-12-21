<template>
    <section class="sustainability-section">
      <!-- Parallax Background -->
      <div class="parallax-container" :style="{ backgroundImage: `url(${parallaxBackground})` }">
        <div class="parallax-content">
          <h2 class="sustainability-title">Our Commitment to Sustainability</h2>
          <p class="sustainability-subtitle">
            We believe in a sustainable future. Here’s how we’re making a difference.
          </p>
        </div>
      </div>
  
      <!-- Sustainability Initiatives -->
      <div class="sustainability-initiatives">
        <!-- Each Initiative Card -->
        <div v-for="(initiative, index) in initiatives" :key="index" class="initiative-card">
          <img :src="initiative.icon" :alt="initiative.title" class="initiative-icon" />
          <h3 class="initiative-title">{{ initiative.title }}</h3>
          <p class="initiative-description">{{ initiative.description }}</p>
        </div>
      </div>
    </section>
  </template>
  <script>
  export default {
    data() {
      return {
        parallaxBackground: ('https://picsum.photos/536/354'), // Example background image require
        initiatives: [
          {
            //  icon: require(' @/assets/icons/recycled-packaging.svg'),
            title: "Recycled Packaging",
            description: "We use 100% recycled and recyclable packaging to reduce waste.",
          },
          {
            // icon: require('@/assets/icons/eco-materials.svg'),
            title: "Eco-friendly Materials",
            description: "Our products are made from sustainable, eco-friendly materials.",
          },
          {
            // icon: require('@/assets/icons/carbon-footprint.svg'),
            title: "Carbon Footprint Reduction",
            description: "We aim to reduce our carbon footprint with every product.",
          },
          {
            //  icon: require('@/assets/icons/energy-efficiency.svg'),
            title: "Energy Efficiency",
            description: "Our facilities use renewable energy to reduce environmental impact.",
          },
        ],
      };
    },
  };
  </script>
  <style scoped>
  /* Sustainability Section Styles */
  .sustainability-section {
    font-family: 'Arial', sans-serif;
  }
  
  /* Parallax Container */
  .parallax-container {
    background-attachment: fixed;
    background-size: cover;
    background-position: center;
    height: 400px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    text-align: center;
    padding: 2rem;
    position: relative;
  }
  
  .parallax-content {
    position: relative;
    z-index: 1;
  }
  
  .sustainability-title {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);
  }
  
  .sustainability-subtitle {
    font-size: 1.2rem;
    margin-bottom: 2rem;
  }
  
  /* Sustainability Initiatives */
  .sustainability-initiatives {
    display: flex;
    justify-content: space-around;
    padding: 3rem;
    background-color: #f9f9f9;
    gap: 2rem;
  }
  
  .initiative-card {
    background-color: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    text-align: center;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .initiative-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
  }
  
  .initiative-icon {
    width: 80px;
    margin-bottom: 1rem;
  }
  
  .initiative-title {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }
  
  .initiative-description {
    font-size: 1rem;
    color: #666;
  }
  
  /* Animations */
  @keyframes parallaxSlide {
    0% {
      transform: translateY(0);
    }
    100% {
      transform: translateY(-30px);
    }
  }
  
  /* Responsive Styles */
  @media (max-width: 768px) {
    .sustainability-section {
      padding: 0;
    }
  
    .parallax-container {
      background-attachment: scroll; /* Disable parallax for mobile */
      height: 250px;
    }
  
    .sustainability-title {
      font-size: 2rem;
    }
  
    .sustainability-subtitle {
      font-size: 1rem;
    }
  
    .sustainability-initiatives {
      flex-direction: column;
      padding: 2rem;
    }
  
    .initiative-card {
      margin-bottom: 1.5rem;
    }
  }
  </style>
  