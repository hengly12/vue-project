<template>
  <div class="home-page">
    <!-- Navbar -->
    <nav class="navbar">
      <div class="container">
        <div class="nav-content">
          <div class="logo">
            <span class="logo-icon">🛒</span>
            <span class="logo-text">ShopHub</span>
          </div>

          <ul class="nav-links" :class="{ active: mobileMenuOpen }">
            <li><router-link to="/home">Home</router-link></li>
            <li><router-link to="/about">About</router-link></li>
            <li><router-link to="/deals">Deals</router-link></li>
            <li><router-link to="/contact">Contact</router-link></li>
          </ul>

          <div class="nav-actions">
            <button class="icon-btn">🔍</button>
            <button class="icon-btn cart-btn">
              🛒
              <span v-if="cartCount > 0" class="cart-badge">{{ cartCount }}</span>
            </button>
          </div>

          <button class="mobile-toggle" @click="toggleMobileMenu">
            {{ mobileMenuOpen ? '✕' : '☰' }}
          </button>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
      <div class="container">
        <div class="hero-content">
          <h1 class="hero-title">Welcome to ShopHub</h1>
          <p class="hero-subtitle">Discover amazing products at unbeatable prices</p>
          <div class="hero-buttons">
            <button class="btn btn-primary">Shop Now</button>
            <button class="btn btn-secondary">Learn More</button>
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features">
      <div class="container">
        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon">📦</div>
            <h3>Free Shipping</h3>
            <p>On orders over $50</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon">🔒</div>
            <h3>Secure Payment</h3>
            <p>100% secure transactions</p>
          </div>
          <div class="feature-card">
            <div class="feature-icon">📈</div>
            <h3>Best Prices</h3>
            <p>Guaranteed lowest prices</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Categories Section -->
    <section class="categories">
      <div class="container">
        <h2 class="section-title">Shop by Category</h2>
        <div class="categories-grid">
          <div 
            v-for="category in categories" 
            :key="category.name"
            class="category-card"
          >
            <div class="category-icon">{{ category.icon }}</div>
            <h3>{{ category.name }}</h3>
            <p>{{ category.count }} items</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Products Section -->
    <section class="products">
      <div class="container">
        <h2 class="section-title">Featured Products</h2>
        <div class="products-grid">
          <div 
            v-for="product in featuredProducts" 
            :key="product.id"
            class="product-card"
          >
            <div class="product-image">{{ product.image }}</div>
            <div class="product-info">
              <span class="product-category">{{ product.category }}</span>
              <h3 class="product-name">{{ product.name }}</h3>
              <div class="product-rating">
                <span class="star">⭐</span>
                <span>{{ product.rating }}</span>
              </div>
              <div class="product-footer">
                <span class="product-price">${{ product.price }}</span>
                <button @click="addToCart(product)" class="btn-add-cart">
                  Add to Cart
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Newsletter Section -->
    <section class="newsletter">
      <div class="container">
        <div class="newsletter-content">
          <h2>Subscribe to Our Newsletter</h2>
          <p>Get the latest deals and exclusive offers delivered to your inbox</p>
          <div class="newsletter-form">
            <input 
              type="email" 
              v-model="email"
              placeholder="Enter your email" 
              class="email-input"
            />
            <button @click="subscribe" class="btn btn-primary">Subscribe</button>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <div class="footer-grid">
          <div class="footer-col">
            <div class="footer-logo">
              <span class="logo-icon">🛒</span>
              <span class="logo-text">ShopHub</span>
            </div>
            <p>Your one-stop shop for all your needs. Quality products at amazing prices.</p>
          </div>

          <div class="footer-col">
            <h3>Quick Links</h3>
            <ul>
              <li><a href="#about">About Us</a></li>
              <li><a href="#shop">Shop</a></li>
              <li><a href="#blog">Blog</a></li>
              <li><a href="#contact">Contact</a></li>
            </ul>
          </div>

          <div class="footer-col">
            <h3>Customer Service</h3>
            <ul>
              <li><a href="#help">Help Center</a></li>
              <li><a href="#track">Track Order</a></li>
              <li><a href="#returns">Returns</a></li>
              <li><a href="#shipping">Shipping Info</a></li>
            </ul>
          </div>

          <div class="footer-col">
            <h3>Contact Info</h3>
            <ul>
              <li>Email: support@shophub.com</li>
              <li>Phone: (555) 123-4567</li>
              <li>Address: 123 Commerce St</li>
              <li>City, State 12345</li>
            </ul>
          </div>
        </div>

        <div class="footer-bottom">
          <p>&copy; 2025 ShopHub. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      mobileMenuOpen: false,
      cartCount: 0,
      email: '',
      categories: [
        { name: 'Electronics', icon: '💻', count: 234 },
        { name: 'Fashion', icon: '👕', count: 456 },
        { name: 'Home & Living', icon: '🏠', count: 189 },
        { name: 'Sports', icon: '⚽', count: 167 }
      ],
      featuredProducts: [
        { id: 1, name: 'Wireless Headphones', price: 79.99, rating: 4.5, image: '🎧', category: 'Electronics' },
        { id: 2, name: 'Smart Watch', price: 199.99, rating: 4.8, image: '⌚', category: 'Electronics' },
        { id: 3, name: 'Laptop Backpack', price: 49.99, rating: 4.3, image: '🎒', category: 'Accessories' },
        { id: 4, name: 'Portable Charger', price: 29.99, rating: 4.6, image: '🔋', category: 'Electronics' }
      ]
    };
  },
  methods: {
    toggleMobileMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen;
    },
    addToCart(product) {
      this.cartCount++;
      console.log('Added to cart:', product.name);
    },
    subscribe() {
      if (this.email) {
        alert(`Subscribed with email: ${this.email}`);
        this.email = '';
      }
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.home-page {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  color: #333;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Navbar */
.navbar {
  background: white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.nav-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 70px;
}

.logo {
  display: flex;
  align-items: center;
  font-size: 24px;
  font-weight: bold;
  color: #2563eb;
}

.logo-icon {
  font-size: 32px;
  margin-right: 8px;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 32px;
}

.nav-links li a {
  text-decoration: none;
  color: #4b5563;
  font-weight: 500;
  transition: color 0.3s;
}

.nav-links li a:hover {
  color: #2563eb;
}

.nav-actions {
  display: flex;
  gap: 12px;
}

.icon-btn {
  background: transparent;
  border: none;
  font-size: 20px;
  cursor: pointer;
  padding: 8px;
  border-radius: 50%;
  transition: background 0.3s;
}

.icon-btn:hover {
  background: #f3f4f6;
}

.cart-btn {
  position: relative;
}

.cart-badge {
  position: absolute;
  top: 0;
  right: 0;
  background: #ef4444;
  color: white;
  font-size: 10px;
  padding: 2px 6px;
  border-radius: 10px;
  font-weight: bold;
}

.mobile-toggle {
  display: none;
  background: transparent;
  border: none;
  font-size: 28px;
  cursor: pointer;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #2563eb 0%, #7c3aed 100%);
  color: white;
  padding: 100px 0;
  text-align: center;
}

.hero-title {
  font-size: 48px;
  margin-bottom: 16px;
  font-weight: bold;
}

.hero-subtitle {
  font-size: 24px;
  margin-bottom: 32px;
  opacity: 0.9;
}

.hero-buttons {
  display: flex;
  gap: 16px;
  justify-content: center;
}

.btn {
  padding: 14px 32px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
}

.btn-primary {
  background: white;
  color: #2563eb;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.btn-secondary {
  background: transparent;
  color: white;
  border: 2px solid white;
}

.btn-secondary:hover {
  background: white;
  color: #2563eb;
}

/* Features Section */
.features {
  padding: 60px 0;
  background: #f9fafb;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 32px;
}

.feature-card {
  background: white;
  padding: 32px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.feature-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
}

.feature-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.feature-card h3 {
  font-size: 20px;
  margin-bottom: 8px;
  color: #1f2937;
}

.feature-card p {
  color: #6b7280;
}

/* Categories Section */
.categories {
  padding: 60px 0;
}

.section-title {
  font-size: 36px;
  font-weight: bold;
  margin-bottom: 40px;
  color: #1f2937;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 24px;
}

.category-card {
  background: white;
  padding: 32px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: all 0.3s;
}

.category-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
}

.category-icon {
  font-size: 56px;
  margin-bottom: 16px;
}

.category-card h3 {
  font-size: 18px;
  margin-bottom: 8px;
  color: #1f2937;
}

.category-card p {
  color: #6b7280;
  font-size: 14px;
}

/* Products Section */
.products {
  padding: 60px 0;
  background: #f9fafb;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 24px;
}

.product-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: all 0.3s;
}

.product-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
}

.product-image {
  background: linear-gradient(135deg, #dbeafe 0%, #e9d5ff 100%);
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80px;
}

.product-info {
  padding: 20px;
}

.product-category {
  color: #2563eb;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
}

.product-name {
  font-size: 18px;
  margin: 8px 0;
  color: #1f2937;
}

.product-rating {
  display: flex;
  align-items: center;
  gap: 4px;
  margin-bottom: 16px;
  color: #6b7280;
  font-size: 14px;
}

.star {
  color: #fbbf24;
}

.product-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.product-price {
  font-size: 24px;
  font-weight: bold;
  color: #1f2937;
}

.btn-add-cart {
  background: #2563eb;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.3s;
}

.btn-add-cart:hover {
  background: #1d4ed8;
}

/* Newsletter Section */
.newsletter {
  background: #1f2937;
  color: white;
  padding: 60px 0;
}

.newsletter-content {
  text-align: center;
}

.newsletter-content h2 {
  font-size: 32px;
  margin-bottom: 16px;
}

.newsletter-content p {
  color: #d1d5db;
  margin-bottom: 32px;
}

.newsletter-form {
  display: flex;
  gap: 12px;
  max-width: 500px;
  margin: 0 auto;
}

.email-input {
  flex: 1;
  padding: 14px 20px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
}

.email-input:focus {
  outline: 2px solid #2563eb;
}

/* Footer */
.footer {
  background: #111827;
  color: #d1d5db;
  padding: 60px 0 20px;
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 40px;
  margin-bottom: 40px;
}

.footer-logo {
  display: flex;
  align-items: center;
  font-size: 20px;
  font-weight: bold;
  color: white;
  margin-bottom: 16px;
}

.footer-col h3 {
  color: white;
  font-size: 18px;
  margin-bottom: 16px;
}

.footer-col ul {
  list-style: none;
}

.footer-col ul li {
  margin-bottom: 12px;
}

.footer-col ul li a {
  color: #d1d5db;
  text-decoration: none;
  transition: color 0.3s;
}

.footer-col ul li a:hover {
  color: #2563eb;
}

.footer-bottom {
  border-top: 1px solid #374151;
  padding-top: 20px;
  text-align: center;
  color: #9ca3af;
}

/* Responsive Design */
@media (max-width: 768px) {
  .nav-links {
    display: none;
    position: absolute;
    top: 70px;
    left: 0;
    right: 0;
    background: white;
    flex-direction: column;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  .nav-links.active {
    display: flex;
  }

  .mobile-toggle {
    display: block;
  }

  .nav-actions {
    display: none;
  }

  .hero-title {
    font-size: 32px;
  }

  .hero-subtitle {
    font-size: 18px;
  }

  .hero-buttons {
    flex-direction: column;
    align-items: center;
  }

  .newsletter-form {
    flex-direction: column;
  }

  .section-title {
    font-size: 28px;
  }
}
</style>