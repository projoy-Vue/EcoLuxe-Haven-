<template>
    <section class="hero-section" @scroll="handleScroll">
      <div class="overlay"></div>
  
      <!-- Background Video/Image -->
      <video
        v-if="videoUrl"
        autoplay
        muted
        loop
        playsinline
        class="hero-video"
        aria-label="Background video of nature"
      >
        <source :src="videoUrl" type="video/mp4" />
      </video>
      <img
        v-if="!videoUrl"
        :src="imageUrl"
        alt="Eco-friendly living background"
        class="hero-image"
      />
  
      <!-- Hero Content -->
      <div class="hero-content">
        <h1 class="hero-title" v-bind:class="{ 'fade-in': titleVisible }">
          Discover Sustainable Living
        </h1>
        <p class="hero-subtitle" v-bind:class="{ 'slide-in': subtitleVisible }">
          Eco-friendly products crafted for a greener future
        </p>
        <div class="cta-buttons">
          <button
            class="primary-cta"
            @mouseover="hoverPrimary"
            aria-label="Shop eco-friendly products"
          >
            Shop Now
          </button>
          <button
            class="secondary-cta"
            @click="scrollToAbout"
            aria-label="Explore our mission"
          >
            Explore Our Mission
          </button>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        videoUrl: '', // Add your video URL here
        imageUrl: 'https://picsum.photos/536/354', // Fallback image URL
        titleVisible: false,
        subtitleVisible: false,
        scrollPosition: 0,
      };
    },
    mounted() {
      setTimeout(() => {
        this.titleVisible = true;
      }, 500);
      setTimeout(() => {
        this.subtitleVisible = true;
      }, 1000);
      window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
      hoverPrimary() {
        // Optional hover effect for primary button
      },
      scrollToAbout() {
        const aboutSection = document.getElementById('about-section');
        aboutSection.scrollIntoView({ behavior: 'smooth' });
      },
      handleScroll() {
        this.scrollPosition = window.scrollY;
        document.querySelector('.hero-video, .hero-image').style.transform = `translateY(${this.scrollPosition * 0.3}px)`;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Hero Section */
  .hero-section {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    overflow: hidden;
    color: white;
  }
  
  .hero-video,
  .hero-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
    transition: transform 0.5s ease-out;
  }
  
  /* Overlay for better readability */
  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4); /* Dark overlay */
    z-index: 0;
  }
  
  /* Hero Content Styling */
  .hero-content {
    z-index: 1;
    padding: 20px;
  }
  
  .hero-title {
    font-size: 4rem;
    font-weight: 700;
    margin: 0;
    opacity: 0;
    transform: translateY(-20px);
    transition: opacity 1.5s ease, transform 1.5s ease;
  }
  
  .hero-title.fade-in {
    opacity: 1;
    transform: translateY(0);
  }
  
  .hero-subtitle {
    font-size: 1.8rem;
    margin: 20px 0;
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 1.5s ease, transform 1.5s ease;
  }
  
  .hero-subtitle.slide-in {
    opacity: 1;
    transform: translateY(0);
  }
  
  /* CTA Buttons */
  .cta-buttons {
    display: flex;
    gap: 20px;
    margin-top: 20px;
  }
  
  .primary-cta,
  .secondary-cta {
    padding: 15px 30px;
    font-size: 1.2rem;
    border: none;
    cursor: pointer;
    transition: all 0.3s ease;
    border-radius: 30px;
  }
  
  .primary-cta {
    background-color: #4CAF50;
    color: white;
  }
  
  .primary-cta:hover {
    background-color: #45a049;
    transform: translateY(-2px);
  }
  
  .secondary-cta {
    background-color: transparent;
    color: white;
    border: 2px solid white;
  }
  
  .secondary-cta:hover {
    background-color: white;
    color: #333;
  }
  
  /* Responsive Design */
  @media screen and (max-width: 768px) {
    .hero-title {
      font-size: 2.5rem;
    }
    .hero-subtitle {
      font-size: 1.2rem;
    }
    .cta-buttons {
      flex-direction: column;
    }
    .primary-cta,
    .secondary-cta {
      width: 100%;
      margin: 10px 0;
    }
  }
  </style>
  