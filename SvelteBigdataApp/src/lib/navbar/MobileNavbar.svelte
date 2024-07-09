<script>
    import home from '../../assets/home.png';
    import product from '../../assets/product.png';
    import info from '../../assets/info.png';
    import contact from '../../assets/contact.png';
  </script>
  
  <header class="mobile-header">
    <h1 class="mobile-logo">Master Store</h1>
    <nav class="mobile-nav">
      <a href="#" class="page-link">
        <img src={home} alt="home" class="page-link-logo" />
        <p class="page-link-title">home</p>
      </a>
      <a href="#" class="page-link">
        <img src={product} alt="product" class="page-link-logo" />
        <p class="page-link-title">product</p>
      </a>
      <a href="#" class="page-link">
        <img src={info} alt="info" class="page-link-logo" />
        <p class="page-link-title">About</p>
      </a>
      <a href="#" class="page-link">
        <img src={contact} alt="contact" class="page-link-logo" />
        <p class="page-link-title">contact</p>
      </a>
    </nav>
  </header>