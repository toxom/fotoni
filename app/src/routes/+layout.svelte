<script>
	import { page } from '$app/stores';
  </script>
  
  <svelte:head>
	<title>Fotoni - Professional Photography & Drone Services</title>
	<meta name="description" content="Premium photography and drone footage services by Fotoni" />
  </svelte:head>
  
  <div class="site-container">
	<header>
	  <div class="header-content">
		<div class="logo">
		  <a href="/">
			<h1>Fotoni</h1>
		  </a>
		</div>
		<nav>
		  <ul>
			<li class:active={$page.url.pathname === '/'}>
			  <a href="/">Home</a>
			</li>
			<li class:active={$page.url.pathname === '/services'}>
			  <a href="/services">Services</a>
			</li>
			<li class:active={$page.url.pathname === '/portfolio'}>
			  <a href="/portfolio">Portfolio</a>
			</li>
			<li class:active={$page.url.pathname === '/about'}>
			  <a href="/about">About</a>
			</li>
			<li class:active={$page.url.pathname === '/contact'}>
			  <a href="/contact">Contact</a>
			</li>
		  </ul>
		</nav>
	  </div>
	</header>
  
	<main>
	  <slot />
	</main>
  
	<footer>
	  <div class="footer-content">
		<div class="footer-section">
		  <h3>Fotoni</h3>
		  <p>Professional photography and drone services capturing your moments from unique perspectives.</p>
		</div>
		
		<div class="footer-section">
		  <h3>Contact</h3>
		  <p>Email: info@fotoni.example</p>
		  <p>Phone: +123 456 7890</p>
		</div>
		
		<div class="footer-section">
		  <h3>Follow Us</h3>
		  <div class="social-links">
			<a href="https://instagram.com" target="_blank" rel="noopener">Instagram</a>
			<a href="https://facebook.com" target="_blank" rel="noopener">Facebook</a>
			<a href="https://youtube.com" target="_blank" rel="noopener">YouTube</a>
		  </div>
		</div>
	  </div>
	  
	  <div class="copyright">
		<p>&copy; {new Date().getFullYear()} Fotoni. All rights reserved.</p>
	  </div>
	</footer>
  </div>
  
  <style>
	:global(body) {
	  margin: 0;
	  padding: 0;
	  font-family: 'Merriweather', sans-serif;
	  color: #333;
	  background-color: #f9f9f9;
	}
  
	.site-container {
	  display: flex;
	  flex-direction: column;
	  min-height: 100vh;
	}
  
	header {
	  background-color: #fff;
	  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
	  position: sticky;
	  top: 0;
	  z-index: 100;
	}
  
	.header-content {
	  max-width: 1200px;
	  margin: 0 auto;
	  padding: 1rem;
	  display: flex;
	  justify-content: space-between;
	  align-items: center;
	}
  
	.logo h1 {
	  margin: 0;
	  font-size: 1.8rem;
	  font-weight: 700;
	  color: #2c3e50;
	}
  
	.logo a {
	  text-decoration: none;
	  color: inherit;
	}
  
	nav ul {
	  display: flex;
	  list-style: none;
	  margin: 0;
	  padding: 0;
	  gap: 2rem;
	}
  
	nav a {
	  text-decoration: none;
	  color: #555;
	  font-weight: 500;
	  transition: color 0.3s ease;
	}
  
	nav a:hover {
	  color: #3498db;
	}
  
	nav li.active a {
	  color: #3498db;
	}
  
	main {
	  flex: 1;
	  max-width: 1200px;
	  margin: 0 auto;
	  padding: 2rem 1rem;
	  width: 100%;
	  box-sizing: border-box;
	}
  
	footer {
	  background-color: #2c3e50;
	  color: #ecf0f1;
	  padding: 3rem 1rem 1rem;
	  margin-top: auto;
	}
  
	.footer-content {
	  max-width: 1200px;
	  margin: 0 auto;
	  display: grid;
	  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
	  gap: 2rem;
	}
  
	.footer-section h3 {
	  margin-top: 0;
	  font-size: 1.2rem;
	  font-weight: 600;
	  margin-bottom: 1rem;
	  color: #ecf0f1;
	}
  
	.social-links {
	  display: flex;
	  gap: 1rem;
	  flex-wrap: wrap;
	}
  
	.social-links a {
	  color: #bdc3c7;
	  text-decoration: none;
	  transition: color 0.3s ease;
	}
  
	.social-links a:hover {
	  color: #3498db;
	}
  
	.copyright {
	  text-align: center;
	  padding-top: 2rem;
	  margin-top: 2rem;
	  border-top: 1px solid rgba(255, 255, 255, 0.1);
	  font-size: 0.9rem;
	  color: #bdc3c7;
	}
  
	@media (max-width: 768px) {
	  .header-content {
		flex-direction: column;
		padding: 1rem;
	  }
  
	  nav ul {
		margin-top: 1rem;
		flex-wrap: wrap;
		justify-content: center;
		gap: 1rem;
	  }
	  
	  .footer-content {
		grid-template-columns: 1fr;
	  }
	}
  </style>