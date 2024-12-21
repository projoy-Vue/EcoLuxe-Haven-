<template>
    <footer class="footer">
      <div class="footer-container">
        <!-- Company Info -->
        <div class="footer-section company-info">
          <h3 class="footer-heading">Company Info</h3>
          <ul>
            <li><a href="#">About Us</a></li>
            <li><a href="#">Careers</a></li>
            <li><a href="#">Press</a></li>
            <li><a href="#">Sustainability</a></li>
          </ul>
        </div>
  
        <!-- Categories -->
        <div class="footer-section categories">
          <h3 class="footer-heading">Categories</h3>
          <ul>
            <li><a href="#">Clothing</a></li>
            <li><a href="#">Tech</a></li>
            <li><a href="#">Home Goods</a></li>
            <li><a href="#">Eco-friendly</a></li>
          </ul>
        </div>
  
        <!-- Customer Service -->
        <div class="footer-section customer-service">
          <h3 class="footer-heading">Customer Service</h3>
          <ul>
            <li><a href="#">Help Center</a></li>
            <li><a href="#">Returns</a></li>
            <li><a href="#">Shipping Info</a></li>
            <li><a href="#">Contact Us</a></li>
          </ul>
        </div>
  
        <!-- Newsletter Signup -->
        <div class="footer-section newsletter">
          <h3 class="footer-heading">Join Our Newsletter</h3>
          <form @submit.prevent="submitNewsletter">
            <input 
              v-model="email" 
              type="email" 
              placeholder="Your Email Address" 
              required 
              class="newsletter-input"
            />
            <button type="submit" class="newsletter-submit">Subscribe</button>
          </form>
          <p v-if="submitted" class="newsletter-confirmation">Thank you for subscribing!</p>
        </div>
  
        <!-- Social Media Links -->
        <div class="footer-section social-media">
          <h3 class="footer-heading">Follow Us</h3>
          <div class="social-icons">
            <a href="#"><i class="fab fa-facebook"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
            <a href="#"><i class="fab fa-instagram"></i></a>
            <a href="#"><i class="fab fa-linkedin"></i></a>
          </div>
        </div>
      </div>
    </footer>
  </template>
  <script>
  export default {
    data() {
      return {
        email: '',
        submitted: false,
      };
    },
    methods: {
      submitNewsletter() {
        // Simulate a successful submission
        this.submitted = true;
        setTimeout(() => {
          this.email = '';
          this.submitted = false;
        }, 3000);
      },
    },
  };
  </script>
 <style scoped>
 /* Footer General Styles */
 .footer {
   background-color: #222;
   color: white;
   padding: 3rem 1.5rem;
   font-family: 'Arial', sans-serif;
 }
 
 .footer-container {
   display: grid;
   grid-template-columns: repeat(5, 1fr);
   gap: 2rem;
 }
 
 /* Footer Section Headings */
 .footer-heading {
   font-size: 1.2rem;
   margin-bottom: 1rem;
   text-transform: uppercase;
   font-weight: bold;
 }
 
 /* Footer Links */
 .footer-section ul {
   list-style: none;
   padding: 0;
 }
 
 .footer-section ul li {
   margin-bottom: 0.5rem;
 }
 
 .footer-section ul li a {
   color: #ccc;
   text-decoration: none;
   transition: color 0.3s ease;
 }
 
 .footer-section ul li a:hover {
   color: #fff;
 }
 
 /* Newsletter Signup */
 .newsletter-input {
   padding: 0.5rem;
   width: 100%;
   margin-bottom: 0.5rem;
   border: none;
   border-radius: 25px;
 }
 .newsletter-input:focus{
  outline: none;
  border:  3px solid #4CAF50;

 }
 .newsletter-submit {
   padding: 0.5rem 1rem;
   background-color: #4CAF50;
   color: white;
   border: none;
   cursor: pointer;
   transition: background-color 0.3s ease;
   width: 100%;
 }
 
 .newsletter-submit:hover {
   background-color: #45A049;
 }
 
 .newsletter-confirmation {
   margin-top: 1rem;
   color: #4CAF50;
 }
 
 /* Social Media Icons */
 .social-icons a {
   color: white;
   margin-right: 1rem;
   font-size: 1.5rem;
   transition: transform 0.3s ease, color 0.3s ease;
 }
 
 .social-icons a:hover {
   transform: scale(1.2);
   color: #4CAF50;
 }
 
 /* Responsive Footer: Mobile View */
 @media (max-width: 768px) {
   .footer-container {
     grid-template-columns: 1fr;
   }
 
   /* Accordion for Mobile */
   .footer-section {
     margin-bottom: 1.5rem;
   }
 
   .footer-heading {
     cursor: pointer;
     position: relative;
   }
 
   .footer-section ul {
     display: none;
   }
 
   .footer-section.active ul {
     display: block;
   }
 }
 </style>
 
  