<template>
    <div>
      <!-- Newsletter Signup Form Section -->
      <section class="newsletter-section">
        <div class="newsletter-container">
          <h2 class="newsletter-title">Stay Updated!</h2>
          <p class="newsletter-text">Subscribe to our newsletter for the latest updates and promotions.</p>
  
          <!-- Form Container with Animation -->
          <form class="newsletter-form" @submit.prevent="handleSubmit">
            <!-- Email Input Field with Real-time Validation -->
            <div class="form-group">
              <input
                type="email"
                v-model="email"
                @input="validateEmail"
                placeholder="Enter your email"
                class="email-input"
              />
              <span v-if="validEmail" class="validation-check">✔️</span>
            </div>
  
            <!-- GDPR Compliance Checkbox -->
            <div class="form-group gdpr">
              <input type="checkbox" v-model="gdprChecked" id="gdpr" />
              <label for="gdpr">I agree to receive promotional emails</label>
            </div>
  
            <!-- Submit Button -->
            <button
              type="submit"
              :disabled="!validEmail || !gdprChecked"
              class="subscribe-button"
            >
              Subscribe
            </button>
  
            <!-- Success Message -->
            <p v-if="showSuccess" class="success-message">Thank you for subscribing!</p>
          </form>
        </div>
      </section>
  
      <!-- Modal for Mobile (optional) -->
      <div v-if="showModal" class="newsletter-modal">
        <div class="modal-content">
          <span class="close-btn" @click="showModal = false">&times;</span>
          <h2>Stay Updated!</h2>
          <form @submit.prevent="handleSubmit">
            <div class="form-group">
              <input
                type="email"
                v-model="email"
                @input="validateEmail"
                placeholder="Enter your email"
                class="email-input"
              />
              <span v-if="validEmail" class="validation-check">✔️</span>
            </div>
  
            <div class="form-group gdpr">
              <input type="checkbox" v-model="gdprChecked" id="modal-gdpr" />
              <label for="modal-gdpr">I agree to receive promotional emails</label>
            </div>
  
            <button
              type="submit"
              :disabled="!validEmail || !gdprChecked"
              class="subscribe-button"
            >
              Subscribe
            </button>
  
            <p v-if="showSuccess" class="success-message">Thank you for subscribing!</p>
          </form>
        </div>
      </div>
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        email: "",
        validEmail: false,
        gdprChecked: false,
        showSuccess: false,
        showModal: false,
      };
    },
    methods: {
      validateEmail() {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        this.validEmail = emailRegex.test(this.email);
      },
      handleSubmit() {
        if (this.validEmail && this.gdprChecked) {
          this.showSuccess = true;
          this.email = ""; // Reset the email field
          this.gdprChecked = false; // Reset the checkbox
          setTimeout(() => {
            this.showSuccess = false;
          }, 3000); // Hide the success message after 3 seconds
        }
      },
    },
  };
  </script>
  <style scoped>
  /* Newsletter Section Styles */
  .newsletter-section {
    background-color: #f3f3f3;
    padding: 2rem;
    text-align: center;
    border-radius: 8px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    animation: fadeIn 1s ease-in-out;
  }
  
  .newsletter-container {
    max-width: 500px;
    margin: 0 auto;
  }
  
  .newsletter-title {
    font-size: 2rem;
    margin-bottom: 1rem;
  }
  
  .newsletter-text {
    font-size: 1rem;
    margin-bottom: 1.5rem;
  }
  
  .newsletter-form {
    display: flex;
    flex-direction: column;
  }
  
  .form-group {
    position: relative;
    margin-bottom: 1rem;
  }
  
  .email-input {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 1rem;
    transition: border-color 0.3s ease;
  }
  
  .email-input:focus {
    border-color: #6ab04c;
  }
  
  .validation-check {
    position: absolute;
    right: 10px;
    top: 50%;
    transform: translateY(-50%);
    color: #6ab04c;
    font-size: 1.2rem;
  }
  
  .gdpr {
    text-align: left;
    margin-bottom: 1.5rem;
  }
  
  .gdpr label {
    font-size: 0.9rem;
    margin-left: 0.5rem;
  }
  
  .subscribe-button {
    background-color: #6ab04c;
    color: white;
    padding: 0.75rem;
    border: none;
    border-radius: 4px;
    font-size: 1.1rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .subscribe-button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  
  .subscribe-button:hover:not(:disabled) {
    background-color: #58a34c;
  }
  
  /* Success Message */
  .success-message {
    color: #6ab04c;
    font-size: 1rem;
    margin-top: 1rem;
    animation: fadeIn 0.5s ease;
  }
  
  /* Modal Styles */
  .newsletter-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }
  
  .modal-content {
    background-color: white;
    padding: 2rem;
    border-radius: 8px;
    max-width: 500px;
    width: 100%;
    text-align: center;
    animation: slideIn 0.5s ease;
  }
  
  .close-btn {
    position: absolute;
    top: 10px;
    right: 15px;
    font-size: 1.5rem;
    cursor: pointer;
    color: #333;
  }
  
  /* Animations */
  @keyframes fadeIn {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  
  @keyframes slideIn {
    0% {
      transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
    }
  }
  
  /* Responsive Styles */
  @media (max-width: 768px) {
    .newsletter-section {
      padding: 1rem;
    }
  
    .email-input {
      font-size: 1rem;
      padding: 0.65rem;
    }
  
    .subscribe-button {
      padding: 0.65rem;
      font-size: 1rem;
    }
  }
  </style>
  