<template>
    <header>
        <nav class="navbar" :class="{ 'sticky': isSticky }">
            <!-- Logo -->
            <div class="logo">
                <a href="/">EcoLuxe Haven</a>
            </div>

            <!-- Desktop Navigation Links -->
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li class="dropdown">
                    <a href="#categories" class="dropdown-toggle">Categories</a>
                    <!-- Mega Menu -->
                    <div class="mega-menu">
                        <div class="mega-menu-column">
                            <h4>Clothing</h4>
                            <ul>
                                <li><a href="#mens">Men's</a></li>
                                <li><a href="#womens">Women's</a></li>
                            </ul>
                            <img src="https://via.placeholder.com/150" alt="Clothing">
                        </div>
                        <div class="mega-menu-column">
                            <h4>Tech</h4>
                            <ul>
                                <li><a href="#gadgets">Gadgets</a></li>
                                <li><a href="#accessories">Accessories</a></li>
                            </ul>
                            <img src="https://via.placeholder.com/150" alt="Tech">
                        </div>
                        <div class="mega-menu-column">
                            <h4>Home Goods</h4>
                            <ul>
                                <li><a href="#furniture">Furniture</a></li>
                                <li><a href="#decor">Decor</a></li>
                            </ul>
                            <img src="https://via.placeholder.com/150" alt="Home Goods">
                        </div>
                    </div>
                </li>
                <li><a href="#about">About</a></li>
            </ul>

            <!-- Search Bar -->
            <div class="search-bar">
                <input type="text" v-model="searchQuery" @input="searchSuggestions" placeholder="Search products..." />
                <ul class="suggestions" v-if="suggestions.length">
                    <li v-for="suggestion in suggestions" :key="suggestion">{{ suggestion }}</li>
                </ul>
            </div>

            <!-- Cart and Account Icons -->
            <div class="icons">
                <div class="cart-icon" @click="toggleCart">
                    <i class="material-icons">shopping_cart</i>
                    <span v-if="cartItemCount > 0" class="cart-count">{{ cartItemCount }}</span>
                    <div class="mini-cart" v-if="isCartOpen">
                        <p v-if="cartItemCount === 0">Your cart is empty</p>
                        <ul v-else>
                            <li v-for="item in cartItems" :key="item.id">{{ item.name }} - {{ item.quantity }}</li>
                        </ul>
                        <button @click="goToCheckout">Checkout</button>
                    </div>
                </div>
                <div class="login-icon" @click="openLogin">
                    <i class="fas fa-user"></i>
                </div>
            </div>

            <!-- Hamburger Menu (Mobile) -->
            <div class="hamburger" @click="toggleMobileMenu">
                <!-- <i class="fas fa-bars"></i> -->
                <span class="hamburger-box">
                    <span class="hamburger-inner"></span>
                </span>
            </div>
        </nav>

        <!-- Full-Screen Mobile Menu Overlay -->
        <div class="mobile-menu" v-if="isMobileMenuOpen">
            <ul>
                <li><a href="#home" @click="toggleMobileMenu">Home</a></li>
                <li><a href="#categories" @click="toggleMobileMenu">Categories</a></li>
                <li><a href="#about" @click="toggleMobileMenu">About</a></li>
                <li @click="toggleCart">Cart</li>
                <li @click="openLogin">Login</li>
            </ul>
        </div>
    </header>
</template>


<script>
export default {
    data() {
        return {
            isSticky: false,
            searchQuery: '',
            suggestions: [],
            cartItems: [
                { id: 1, name: 'Eco-Friendly Shirt', quantity: 2 },
                { id: 2, name: 'Reusable Water Bottle', quantity: 1 },
            ],
            isCartOpen: false,
            cartItemCount: 3,
            isMobileMenuOpen: false,
        };
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            this.isSticky = window.scrollY > 50;
        },
        searchSuggestions() {
            // Fetch suggestions based on `searchQuery` (Mocking suggestions here)
            if (this.searchQuery.length > 2) {
                this.suggestions = ['Eco-Friendly Shirt', 'Bamboo Toothbrush', 'Organic Cotton Towel'];
            } else {
                this.suggestions = [];
            }
        },
        toggleCart() {
            this.isCartOpen = !this.isCartOpen;
        },
        goToCheckout() {
            // Navigate to checkout
        },
        openLogin() {
            // Open login modal
        },
        toggleMobileMenu() {
            this.isMobileMenuOpen = !this.isMobileMenuOpen;
        },
    },
};
</script>

<style scoped>
/* Navbar Styling */
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 30px;
    background-color: transparent;
    transition: background-color 0.3s ease;
    z-index: 100;
}

.navbar.sticky {
    background-color: #333;
}

.logo a {
    font-size: 1.5rem;
    color: white;
    text-decoration: none;
}

.nav-links {
    display: flex;
    list-style: none;
}

.nav-links li {
    margin: 0 15px;
}

.nav-links a {
    color: white;
    text-decoration: none;
    font-size: 1.2rem;
}

.dropdown:hover .mega-menu {
    display: flex;
    z-index: 100;
}

.mega-menu {
    display: none;
    position: absolute;
    top: 70%;
    left: 0;
    background-color: white;
    width: 100vw;
    padding: 20px;
    color: #333;
    justify-content: space-between;
}

.mega-menu-column {
    width: 30%;
}

.mega-menu-column h4 {
    margin-bottom: 10px;
    font-size: 1.2rem;
}

.mega-menu-column ul {
    list-style: none;
    padding: 0;
}

.mega-menu-column li {
    margin-bottom: 5px;
}

.mega-menu-column a {
    color: #333;
    text-decoration: none;
}

.mega-menu-column img {
    width: 100%;
    height: 300px;
    object-fit: cover;
}

/* Search Bar */
.search-bar {
    position: relative;
}

.search-bar input {
    padding: 7px 10px;
    font-size: 1rem;
    border: 3px solid #28a745;
    outline: none;
    border-radius: 25px;
    width: 300px;
}
.suggestions {
    position: absolute;
    top: 100%;
    background: white;
    width: 100%;
    list-style: none;
    padding: 0;
    margin: 0;
}

.suggestions li {
    padding: 10px;
    cursor: pointer;
}

.suggestions li:hover {
    background-color: #f0f0f0;
}

/* Cart and Login Icons */
.icons {
    display: flex;
    gap: 20px;
}

.cart-icon {
    position: relative;
    cursor: pointer;
    margin-right: 20px;
}
.cart-icon i, .login-icon i {
    font-size: 1.7rem;
    color: white;
    width: 30px;
    transition: all 0.3s ease;
}

.cart-icon i:hover, .login-icon i:hover, .cart-count:hover {
    color: #28a745;
    transform: translate(0, -5px);
}
.login-icon {
    color: white;
}

/* Cart Count */
.cart-count {
    position: absolute;
    top: -20px;
    right: -10px;
    background-color: rgb(20, 18, 18);
    color: rgb(250, 244, 244);
    border-radius: 50%;
    padding: 5px 10px;
    font-size: 0.8rem;
    font-weight: bold;
    transition: all 0.3s ease;
}


.mini-cart {
    position: absolute;
    top: 40px;
    right: 0;
    width: 300px;
    background-color: white;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.mini-cart ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

.mini-cart li {
    padding: 10px;
    border-bottom: 1px solid #f0f0f0;
}

/* .mini-cart li:last-child {
    border-bottom: none;
  } */
.mini-cart li:hover {
    background-color: #f0f0f0;
}


.mini-cart button {
    margin-top: 20px;
    width: 100%;
    padding: 10px;
    background-color: #333;
    color: white;
    border: none;
    cursor: pointer;
}

/* Hamburger Menu (Mobile) */
.hamburger {
    display: none;
    cursor: pointer;
}
.mobile-menu {
    position: fixed;
    top: 70px;
    right: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    z-index: 1000;
    display: flex;
    flex-direction: column;
    padding: 50px 20px;
}

.mobile-menu ul {
    list-style: none;
    padding: 0;
}

.mobile-menu li {
    margin: 20px 0;
    font-size: 1.5rem;
}

.mobile-menu a {
    color: white;
    text-decoration: none;
}


@media screen and (max-width: 768px) {
    .nav-links {
        display: none;
    }

   

    .hamburger {
        display: block;
        color: white;
        font-size: 1.5rem;
    }

    .search-bar {
        display: none;
    }
}
</style>