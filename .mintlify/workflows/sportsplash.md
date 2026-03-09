---
name: "Sportsplash"
on:
  push:
    - repo: "mire402/Sport-splash"
context:
  - repo: "mire402/Sport-splash"
---

Turn it into a website that has this code <!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>Sport splash</title>
    <style>
      :root { color-scheme: light; }
      * { box-sizing: border-box; }
      html,body { height: 100%; }
      body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
        background: linear-gradient(#bfbfbf, #a9a9a9);
        color: #111;
        position: relative;
        min-height: 100vh;
        overflow-x: hidden;
      }

      /* realistic gold sides */
      body::before,
      body::after{
        content: '';
        position: fixed;
        top: 0;
        bottom: 0;
        width: 60px;
        z-index: 0;
        pointer-events: none;
        background: linear-gradient(180deg,#ffd96b,#f6c84a 25%,#b8831a 60%,#6b3f0f 100%);
        box-shadow: inset -3px 0 8px rgba(255,255,255,0.2), inset 3px 0 12px rgba(0,0,0,0.25);
        transform: skewX(-6deg);
      }
      body::before{ left: -30px; }
      body::after{ right: -30px; transform: skewX(6deg); }

      .site-header{
        position: sticky; top: 0; z-index: 4;
        display:flex; justify-content:space-between; align-items:center;
        gap:1rem; padding:1rem 1.5rem; background: linear-gradient(90deg,#6b6b6b,#7b7b7b);
        border-bottom: 2px solid rgba(0,0,0,0.12);
      }
      .site-header h1 { margin:0; font-size:1.5rem; text-transform:capitalize; color:#fff; text-shadow:0 1px 0 rgba(0,0,0,0.4); }
      .actions { display:flex; gap:0.6rem; align-items:center; }
      button { cursor:pointer; border:none; border-radius:8px; padding:0.6rem 0.9rem; font-weight:600; background:#fff; }

      main { max-width:1050px; margin:1.2rem auto; padding:0 1rem 2rem; position:relative; z-index:2; }
      .intro { margin-bottom:1rem; }

      .product-grid{ display:grid; grid-template-columns: repeat(auto-fit,minmax(210px,1fr)); gap:1rem; margin-bottom:2rem; }
      .card{ background:linear-gradient(180deg,#fbfbfb,#efefef); border-radius:12px; padding:1rem; box-shadow: 0 6px 18px rgba(0,0,0,0.18); position:relative; }
      .card h3{ margin-top:0; font-size:1.05rem }
      .card .controls{ display:flex; gap:0.5rem; margin-top:0.6rem; }
      .price{ font-weight:700; color:#222; }
      .buy-btn{ background:#1f66ff; color:#fff; padding:0.5rem 0.7rem; border-radius:8px }
      .wish-btn{ background:transparent; font-size:1.1rem; padding:0.4rem; }

      .online-payment{ background:#efefef; border-radius:12px; padding:1rem; box-shadow:0 3px 8px rgba(0,0,0,0.12); }

      #paymentForm{ display:grid; gap:0.8rem; }
      label{ display:grid; gap:0.35rem; }
      input{ border:1px solid #666; border-radius:8px; padding:0.55rem; }
      #message{ margin-top:0.8rem; font-weight:700 }

      /* panels */
      .panel{ position:fixed; top:0; bottom:0; width:320px; background:linear-gradient(#fff,#f4f4f4); box-shadow:0 10px 30px rgba(0,0,0,0.35); z-index:8; transform:translateX(100%); transition:transform .28s ease; display:flex; flex-direction:column; }
      .panel.left{ left:0; transform:translateX(-100%); }
      .panel.right{ right:0; }
      .panel.open.right{ transform:translateX(0); }
      .panel.open.left{ transform:translateX(0); }
      .panel header{ padding:1rem; display:flex; justify-content:space-between; align-items:center; border-bottom:1px solid rgba(0,0,0,0.06); }
      .panel .list{ padding:1rem; overflow:auto; flex:1; }
      .panel .item{ position:relative; display:flex; align-items:center; gap:0.5rem; padding:0.5rem 0; border-bottom:1px dashed rgba(0,0,0,0.06); }
      .panel .remove{ background:#ff4444; color:#fff; border-radius:6px; padding:0.25rem 0.45rem; font-size:0.8rem; }

      .count-badge{ background:#1f66ff; color:#fff; padding:0.15rem 0.5rem; border-radius:999px; font-weight:700; margin-left:4px; font-size:0.85rem; }
    </style>
  </head>
  <body>
    <header class="site-header">
      <h1>Sport splash</h1>
      <div class="actions">
        <button id="cartBtn" aria-label="View shopping cart">🛒 Cart<span id="cartCount" class="count-badge">0</span></button>
        <button id="wishlistBtn" aria-label="View wishlist">💙 Wishlist<span id="wishCount" class="count-badge">0</span></button>
      </div>
    </header>

    <main>
      <section class="intro">
        <h2>Buy products from Sport splash</h2>
        <p>Top devices and sports bundles for your active lifestyle.</p>
      </section>

      <section class="product-grid" id="productGrid">
        <article class="card" data-name="Sport Splash for Golf ball and tennis and etc...">
          <h3>Sport Splash for Golf ball and tennis and etc...</h3>
          <p>Great starter kit for golf, tennis, and more sports activities.</p>
          <p class="price">$13</p>
          <div class="controls">
            <button class="buy-btn" data-name="Sport Splash for Golf ball and tennis and etc...">Add to Cart</button>
            <button class="wish-btn" title="Add to wishlist" data-name="Sport Splash for Golf ball and tennis and etc...">🤍</button>
          </div>
        </article>

        <article class="card" data-name="Sport splash for football and etc.">
          <h3>Sport splash for football and etc.</h3>
          <p>Football-ready bundle with training accessories and extras.</p>
          <p class="price">$24</p>
          <div class="controls">
            <button class="buy-btn" data-name="Sport splash for football and etc.">Add to Cart</button>
            <button class="wish-btn" title="Add to wishlist" data-name="Sport splash for football and etc.">🤍</button>
          </div>
        </article>

        <article class="card" data-name="Sport splash for soccer ball, basketball, and etc...">
          <h3>Sport splash for soccer ball, basketball, and etc...</h3>
          <p>Multi-sport package for soccer, basketball, and additional play.</p>
          <p class="price">$24</p>
          <div class="controls">
            <button class="buy-btn" data-name="Sport splash for soccer ball, basketball, and etc...">Add to Cart</button>
            <button class="wish-btn" title="Add to wishlist" data-name="Sport splash for soccer ball, basketball, and etc...">🤍</button>
          </div>
        </article>

        <article class="card" data-name="Sport splash Rugyball and etc...">
          <h3>Sport splash Rugyball and etc...</h3>
          <p>Rugyball-focused set designed for endurance and impact training.</p>
          <p class="price">$30</p>
          <div class="controls">
            <button class="buy-btn" data-name="Sport splash Rugyball and etc...">Add to Cart</button>
            <button class="wish-btn" title="Add to wishlist" data-name="Sport splash Rugyball and etc...">🤍</button>
          </div>
        </article>
      </section>

      <section class="online-payment" id="onlinePayment">
        <h2>Pay Online (Separate Checkout Area)</h2>
        <p>This is the online payment place for Sport splash purchases.</p>
        <form id="paymentForm">
          <label>Full name <input type="text" name="name" required /></label>
          <label>Email <input type="email" name="email" required /></label>
          <label>Card number <input type="text" name="cardNumber" inputmode="numeric" minlength="12" required /></label>
          <label>Expiry (MM/YY) <input type="text" name="expiry" placeholder="MM/YY" required /></label>
          <label>CVV <input type="password" name="cvv" inputmode="numeric" minlength="3" maxlength="4" required /></label>
          <button type="submit">Pay online with Sport splash</button>
        </form>
        <p id="message" aria-live="polite"></p>
      </section>
    </main>

    <!-- Panels -->
    <aside id="cartPanel" class="panel right" aria-hidden="true">
      <header>
        <strong>Shopping Cart</strong>
        <button id="closeCart" style="background:#ff4444; color:#fff;">Close</button>
      </header>
      <div class="list" id="cartList">Empty</div>
    </aside>

    <aside id="wishlistPanel" class="panel left" aria-hidden="true">
      <header>
        <strong>Wishlist</strong>
        <button id="closeWishlist" style="background:#ff4444; color:#fff;">Close</button>
      </header>
      <div class="list" id="wishlistList">Empty</div>
    </aside>

    <script>
      const cartBtn = document.getElementById('cartBtn');
      const cartCount = document.getElementById('cartCount');
      const cartPanel = document.getElementById('cartPanel');
      const cartList = document.getElementById('cartList');
      const closeCartBtn = document.getElementById('closeCart');
      
      const wishlistBtn = document.getElementById('wishlistBtn');
      const wishCount = document.getElementById('wishCount');
      const wishlistPanel = document.getElementById('wishlistPanel');
      const wishlistList = document.getElementById('wishlistList');
      const closeWishlistBtn = document.getElementById('closeWishlist');
      
      const buyButtons = document.querySelectorAll('.buy-btn');
      const wishButtons = document.querySelectorAll('.wish-btn');
      const paymentForm = document.getElementById('paymentForm');
      const message = document.getElementById('message');

      let cartItems = [];
      let wishlistItems = [];

      function updateCounts() {
        cartCount.textContent = cartItems.length;
        wishCount.textContent = wishlistItems.length;
      }

      function renderList(listEl, items, isCart) {
        if (items.length === 0) { listEl.textContent = 'Empty'; return; }
        listEl.innerHTML = '';
        items.forEach((it, idx) => {
          const row = document.createElement('div');
          row.className = 'item';
          const name = document.createElement('div');
          name.textContent = it;
          const remove = document.createElement('button');
          remove.className = 'remove';
          remove.textContent = 'Remove';
          remove.addEventListener('click', () => {
            items.splice(idx, 1);
            updateCounts();
            if (isCart) renderList(cartList, cartItems, true);
            else renderList(wishlistList, wishlistItems, false);
          });
          row.appendChild(name);
          row.appendChild(remove);
          listEl.appendChild(row);
        });
      }

      // Cart functionality
      buyButtons.forEach(btn => {
        btn.addEventListener('click', () => {
          const name = btn.dataset.name || btn.closest('.card')?.dataset?.name || 'Item';
          cartItems.push(name);
          updateCounts();
          message.textContent = `${name} added to shopping cart.`;
        });
      });

      cartBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        const isOpen = cartPanel.classList.contains('open');
        if (isOpen) {
          cartPanel.classList.remove('open');
          cartPanel.setAttribute('aria-hidden', 'true');
        } else {
          renderList(cartList, cartItems, true);
          cartPanel.classList.add('open');
          cartPanel.setAttribute('aria-hidden', 'false');
        }
      });

      closeCartBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        cartPanel.classList.remove('open');
        cartPanel.setAttribute('aria-hidden', 'true');
      });

      cartPanel.addEventListener('click', (e) => { e.stopPropagation(); });

      // Wishlist functionality
      wishButtons.forEach(btn => {
        btn.addEventListener('click', () => {
          const name = btn.dataset.name || btn.closest('.card')?.dataset?.name || 'Item';
          const index = wishlistItems.indexOf(name);
          if (index === -1) {
            wishlistItems.push(name);
            btn.textContent = '💙';
            message.textContent = `${name} added to wishlist.`;
          } else {
            wishlistItems.splice(index, 1);
            btn.textContent = '🤍';
            message.textContent = `${name} removed from wishlist.`;
          }
          updateCounts();
          renderList(wishlistList, wishlistItems, false);
        });
      });

      wishlistBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        const isOpen = wishlistPanel.classList.contains('open');
        if (isOpen) {
          wishlistPanel.classList.remove('open');
          wishlistPanel.setAttribute('aria-hidden', 'true');
        } else {
          renderList(wishlistList, wishlistItems, false);
          wishlistPanel.classList.add('open');
          wishlistPanel.setAttribute('aria-hidden', 'false');
        }
      });

      closeWishlistBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        wishlistPanel.classList.remove('open');
        wishlistPanel.setAttribute('aria-hidden', 'true');
      });

      wishlistPanel.addEventListener('click', (e) => { e.stopPropagation(); });

      // Close panels when clicking outside
      document.addEventListener('click', () => {
        cartPanel.classList.remove('open');
        cartPanel.setAttribute('aria-hidden', 'true');
        wishlistPanel.classList.remove('open');
        wishlistPanel.setAttribute('aria-hidden', 'true');
      });



      paymentForm.addEventListener('submit', (e) => {
        e.preventDefault();
        if (cartItems.length === 0) {
          message.textContent = 'Please add items to cart before paying.';
          return;
        }
        message.textContent = 'Thank you for buying our product from Sport splash!';
        paymentForm.reset();
        cartItems = [];
        updateCounts();
        renderList(cartList, cartItems, true);
      });
    </script>
   </body>
</html>
