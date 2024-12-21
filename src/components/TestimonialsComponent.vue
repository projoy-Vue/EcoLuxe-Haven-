<template>
    <section class="testimonial-card-carousel">
      <h2 class="section-title">What Our Customers Say</h2>
  
      <!-- Carousel Wrapper -->
      <div class="carousel-container">
        <div
          class="carousel-track"
          :style="`transform: translateX(-${currentSlide * 100}%);`"
        >
          <!-- Testimonial Card -->
          <div
            v-for="(testimonial, index) in testimonials"
            :key="index"
            class="testimonial-card"
          >
            <div class="card-content">
              <img
                :src="testimonial.customerImage"
                :alt="testimonial.customerName"
                class="customer-photo"
              />
              <h3 class="customer-name">{{ testimonial.customerName }}</h3>
              <div class="star-rating">
                <span
                  v-for="star in 5"
                  :key="star"
                  class="star"
                  :class="{ 'filled-star': star <= testimonial.rating }"
                  >★</span
                >
              </div>
              <p class="testimonial-text">{{ testimonial.review }}</p>
            </div>
          </div>
        </div>
      </div>
  
      <!-- Carousel Controls -->
      <div class="carousel-controls">
        <button class="prev-btn" @click="prevSlide">←</button>
        <button class="next-btn" @click="nextSlide">→</button>
      </div>
  
      <!-- Pagination Dots -->
      <div class="carousel-pagination">
        <span
          v-for="(dot, index) in testimonials"
          :key="index"
          class="carousel-dot"
          :class="{ 'active-dot': index === currentSlide }"
          @click="goToSlide(index)"
        ></span>
      </div>
    </section>
  </template>
  <script>
  export default {
    data() {
      return {
        currentSlide: 0,
        testimonials: [
          {
            customerName: "John Doe",
            customerImage: "path_to_john_doe_image.jpg",
            rating: 5,
            review:
              "This product is amazing! I would highly recommend it to everyone!",
          },
          {
            customerName: "Jane Smith",
            customerImage: "path_to_jane_smith_image.jpg",
            rating: 4,
            review: "Great quality and fast delivery. Very satisfied with my purchase!",
          },
          {
            customerName: "Michael Johnson",
            customerImage: "path_to_michael_johnson_image.jpg",
            rating: 5,
            review: "Absolutely love it! Fantastic service and product!",
          },
        ],
      };
    },
    methods: {
      nextSlide() {
        if (this.currentSlide < this.testimonials.length - 1) {
          this.currentSlide++;
        } else {
          this.currentSlide = 0;
        }
      },
      prevSlide() {
        if (this.currentSlide > 0) {
          this.currentSlide--;
        } else {
          this.currentSlide = this.testimonials.length - 1;
        }
      },
      goToSlide(index) {
        this.currentSlide = index;
      },
    },
  };
  </script>
  <style scoped>
  /* Testimonial Card Carousel Styles */
  .testimonial-card-carousel {
    text-align: center;
    padding: 2rem;
    background-color: #f7f7f7;
  }
  
  .section-title {
    font-size: 2.5rem;
    margin-bottom: 1.5rem;
  }
  
  .carousel-container {
    overflow: hidden;
    width: 100%;
    max-width: 800px;
    margin: 0 auto;
  }
  
  .carousel-track {
    display: flex;
    transition: transform 0.5s ease;
  }
  
  .testimonial-card {
    flex: 1 0 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .card-content {
    background-color: #fff;
    padding: 2rem;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    max-width: 600px;
    text-align: left;
  }
  
  .customer-photo {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    margin-bottom: 1rem;
  }
  
  .customer-name {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }
  
  .star-rating {
    margin-bottom: 1rem;
  }
  
  .star {
    font-size: 1.2rem;
    color: #ccc;
  }
  
  .filled-star {
    color: #ffc107;
  }
  
  .testimonial-text {
    font-size: 1rem;
    color: #666;
  }
  
  /* Carousel Controls */
  .carousel-controls {
    margin: 1rem 0;
    display: flex;
    justify-content: center;
    gap: 1rem;
  }
  
  .prev-btn,
  .next-btn {
    background-color: #333;
    color: #fff;
    border: none;
    padding: 0.75rem 1.5rem;
    font-size: 1.2rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .prev-btn:hover,
  .next-btn:hover {
    background-color: #555;
  }
  
  /* Pagination Dots */
  .carousel-pagination {
    display: flex;
    justify-content: center;
    margin-top: 1rem;
  }
  
  .carousel-dot {
    width: 12px;
    height: 12px;
    margin: 0 5px;
    border-radius: 50%;
    background-color: #ccc;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .active-dot {
    background-color: #333;
  }
  
  /* Responsive Design */
  @media (max-width: 768px) {
    .testimonial-card-carousel {
      padding: 1rem;
    }
  
    .card-content {
      padding: 1rem;
    }
  
    .prev-btn,
    .next-btn {
      padding: 0.5rem 1rem;
    }
  
    .customer-photo {
      width: 50px;
      height: 50px;
    }
  
    .testimonial-text {
      font-size: 0.9rem;
    }
  }
  </style>
  