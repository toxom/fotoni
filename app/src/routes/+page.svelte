<script>
    import { onMount } from 'svelte';
  
    let currentSlide = 0;
    let slides = [
      {
        image: 'https://images.unsplash.com/photo-1506953823976-52e1fdc0149a', 
        title: 'Breathtaking Aerial Photography',
        description: 'Capture your world from a new perspective'
      },
      {
        image: 'https://images.unsplash.com/photo-1533747139803-fa0fb3dc5087', 
        title: 'Professional Photo Sessions',
        description: 'Preserving your special moments with artistic flair'
      },
      {
        image: 'https://images.unsplash.com/photo-1524985069026-dd778a71c7b4', 
        title: 'Cinematic Drone Footage',
        description: 'Elevate your visual storytelling'
      }
    ];
  
    onMount(() => {
      const interval = setInterval(() => {
        currentSlide = (currentSlide + 1) % slides.length;
      }, 5000);
  
      return () => clearInterval(interval);
    });
  
    function setSlide(index) {
      currentSlide = index;
    }
  </script>
  
  <div class="hero">
    {#each slides as slide, i}
      <div class="slide" class:active={currentSlide === i} style="background-image: url({slide.image})">
        <div class="slide-content">
          <h2>{slide.title}</h2>
          <p>{slide.description}</p>
          <a href="/contact" class="cta-button">Get a Quote</a>
        </div>
      </div>
    {/each}
    
    <div class="slide-controls">
      {#each slides as _, i}
        <button class="slide-indicator" class:active={currentSlide === i} on:click={() => setSlide(i)}></button>
      {/each}
    </div>
  </div>
  
  <section class="services">
    <h2>Our Services</h2>
    <div class="services-grid">
      <div class="service-card">
        <div class="service-icon">📸</div>
        <h3>Professional Photography</h3>
        <p>Capture your special moments with our professional photography services for events, portraits, and commercial use.</p>
        <a href="/services#photography" class="service-link">Learn More</a>
      </div>
      
      <div class="service-card">
        <div class="service-icon">🚁</div>
        <h3>Drone Footage</h3>
        <p>Get stunning aerial views and cinematic footage of landscapes, properties, events, and more with our expert drone operators.</p>
        <a href="/services#drone" class="service-link">Learn More</a>
      </div>
      
      <div class="service-card">
        <div class="service-icon">✏️</div>
        <h3>Photo Editing</h3>
        <p>Transform your images with our professional editing services, from basic touch-ups to creative artistic enhancements.</p>
        <a href="/services#editing" class="service-link">Learn More</a>
      </div>
    </div>
  </section>
  
  <section class="testimonials">
    <h2>What Our Clients Say</h2>
    <div class="testimonial-grid">
      <div class="testimonial">
        <p>"Fotoni captured our wedding day perfectly. The drone footage gave us perspectives we never thought possible!"</p>
        <div class="client">- Sarah & Tom</div>
      </div>
      
      <div class="testimonial">
        <p>"The aerial photos of our property helped it sell within a week. Professional service and stunning results."</p>
        <div class="client">- Alex, Real Estate Agent</div>
      </div>
      
      <div class="testimonial">
        <p>"Working with Fotoni for our company event was fantastic. They delivered beyond our expectations."</p>
        <div class="client">- Maria, Event Coordinator</div>
      </div>
    </div>
  </section>
  
  <section class="cta">
    <h2>Ready to capture your story?</h2>
    <p>Contact us today to discuss your photography and drone footage needs.</p>
    <div class="cta-buttons">
      <a href="/portfolio" class="secondary-button">View Portfolio</a>
      <a href="/contact" class="primary-button">Get in Touch</a>
    </div>
  </section>
  
  <style>
    .hero {
      position: relative;
      height: 80vh;
      min-height: 500px;
      overflow: hidden;
    }
  
    .slide {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-size: cover;
      background-position: center;
      opacity: 0;
      transition: opacity 1s ease-in-out;
      display: flex;
      align-items: center;
    }
  
    .slide.active {
      opacity: 1;
      z-index: 1;
    }
  
    .slide::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.4);
    }
  
    .slide-content {
      position: relative;
      z-index: 2;
      max-width: 800px;
      margin: 0 auto;
      padding: 0 2rem;
      text-align: center;
      color: white;
    }
  
    .slide-content h2 {
      font-size: 3rem;
      margin-bottom: 1rem;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    }
  
    .slide-content p {
      font-size: 1.5rem;
      margin-bottom: 2rem;
      text-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
    }
  
    .cta-button {
      display: inline-block;
      background: #3498db;
      color: white;
      padding: 0.8rem 2rem;
      border-radius: 50px;
      font-size: 1.1rem;
      text-decoration: none;
      transition: background 0.3s ease, transform 0.2s ease;
    }
  
    .cta-button:hover {
      background: #2980b9;
      transform: translateY(-2px);
    }
  
    .slide-controls {
      position: absolute;
      bottom: 2rem;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 0.8rem;
      z-index: 3;
    }
  
    .slide-indicator {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.5);
      border: none;
      cursor: pointer;
      transition: background 0.3s ease;
    }
  
    .slide-indicator.active {
      background: white;
    }
  
    section {
      padding: 5rem 0;
    }
  
    section h2 {
      text-align: center;
      font-size: 2.2rem;
      margin-bottom: 3rem;
      color: #2c3e50;
    }
  
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1rem;
    }
  
    .service-card {
      background: white;
      border-radius: 10px;
      padding: 2rem;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
      text-align: center;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
  
    .service-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
    }
  
    .service-icon {
      font-size: 3rem;
      margin-bottom: 1.5rem;
    }
  
    .service-card h3 {
      font-size: 1.5rem;
      margin-bottom: 1rem;
      color: #2c3e50;
    }
  
    .service-link {
      display: inline-block;
      margin-top: 1rem;
      color: #3498db;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s ease;
    }
  
    .service-link:hover {
      color: #2980b9;
    }
  
    .testimonials {
      background: #f5f7fa;
    }
  
    .testimonial-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1rem;
    }
  
    .testimonial {
      background: white;
      border-radius: 10px;
      padding: 2rem;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
    }
  
    .testimonial p {
      font-style: italic;
      font-size: 1.1rem;
      color: #34495e;
      margin-bottom: 1.5rem;
      line-height: 1.6;
    }
  
    .client {
      font-weight: 600;
      color: #3498db;
    }
  
    .cta {
      text-align: center;
      background: linear-gradient(to right, #3498db, #2c3e50);
      color: white;
      padding: 5rem 1rem;
    }
  
    .cta h2 {
      color: white;
      margin-bottom: 1rem;
    }
  
    .cta p {
      font-size: 1.2rem;
      margin-bottom: 2rem;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }
  
    .cta-buttons {
      display: flex;
      justify-content: center;
      gap: 1.5rem;
      flex-wrap: wrap;
    }
  
    .primary-button, .secondary-button {
      display: inline-block;
      padding: 0.8rem 2rem;
      border-radius: 50px;
      font-size: 1.1rem;
      text-decoration: none;
      transition: background 0.3s ease, transform 0.2s ease;
    }
  
    .primary-button {
      background: white;
      color: #3498db;
    }
  
    .primary-button:hover {
      background: #f0f5fa;
      transform: translateY(-2px);
    }
  
    .secondary-button {
      background: transparent;
      color: white;
      border: 2px solid white;
    }
  
    .secondary-button:hover {
      background: rgba(255, 255, 255, 0.1);
      transform: translateY(-2px);
    }
  
    @media (max-width: 768px) {
      .slide-content h2 {
        font-size: 2rem;
      }
  
      .slide-content p {
        font-size: 1.1rem;
      }
  
      section {
        padding: 3rem 0;
      }
  
      .service-card, .testimonial {
        padding: 1.5rem;
      }
    }
  </style>