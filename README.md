<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cloudy Bliss Bakery - Order Now! Phone: 7339651100</title>
    <style>
        
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Comic Sans MS', cursive, sans-serif; background: linear-gradient(45deg, #e0f7fa, #f3e5f5); color: #333; min-height: 100vh; }
        .container { max-width: 1200px; margin: 0 auto; padding: 20px; }
        
        header { text-align: center; margin-bottom: 30px; }
        h1 { font-size: 3em; color: #4a90e2; text-shadow: 2px 2px #fff; }
        .tagline { font-size: 1.2em; margin-bottom: 20px; }
        .scrolling-discount { background: #fff3cd; color: #856404; padding: 10px; margin-bottom: 20px; overflow: hidden; white-space: nowrap; }
        .scrolling-discount span { display: inline-block; animation: scroll 30s linear infinite; }
        @keyframes scroll { 0% { transform: translateX(100%); } 100% { transform: translateX(-100%); } }
        .filters { display: flex; justify-content: center; gap: 10px; margin-bottom: 20px; flex-wrap: wrap; }
        .filters button { padding: 10px 20px; border: none; background: #b3d9ff; color: white; border-radius: 20px; cursor: pointer; transition: background 0.3s; }
        .filters button.active { background: #4a90e2; }
        .cart-info { font-weight: bold; color: #8b4513; margin-top: 10px; cursor: pointer; }
        .cart-info:hover { text-decoration: underline; }
        
       
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; }
        .card { background: white; border-radius: 15px; padding: 15px; text-align: center; box-shadow: 0 4px 8px rgba(0,0,0,0.1); cursor: pointer; transition: transform 0.3s; }
        .card:hover { transform: scale(1.05); }
        .card img { width: 100%; height: 150px; object-fit: cover; border-radius: 10px; }
        .card h3 { margin: 10px 0; color: #a0522d; }
        .type { color: #daa520; font-style: italic; }
        .price { font-weight: bold; color: #dc143c; }
        
        
        .overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); display: none; justify-content: center; align-items: center; z-index: 1000; animation: fadeIn 0.5s; }
        .overlay.show { display: flex; }
        .popup { background: white; border-radius: 20px; padding: 20px; max-width: 500px; width: 90%; text-align: center; transform: rotateY(0deg) scale(0.8); animation: pop3D 0.6s ease-out forwards; box-shadow: 0 10px 30px rgba(0,0,0,0.3); position: relative; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes pop3D { 
            0% { transform: rotateY(-90deg) scale(0.5); opacity: 0; } 
            50% { transform: rotateY(-45deg) scale(0.8); opacity: 0.5; } 
            100% { transform: rotateY(0deg) scale(1); opacity: 1; } 
        }
        .popup img { width: 100%; height: 200px; object-fit: cover; border-radius: 10px; margin-bottom: 15px; }
        .popup h2 { color: #a0522d; }
        .popup p { margin: 10px 0; color: #666; }
        .popup .price { font-size: 1.5em; color: #dc143c; }
        .add-btn { background: #32cd32; color: white; border: none; padding: 12px 25px; border-radius: 25px; cursor: pointer; font-size: 1.1em; transition: background 0.3s; }
        .add-btn:hover { background: #228b22; }
        .close { position: absolute; top: 10px; right: 15px; font-size: 30px; cursor: pointer; color: #aaa; }
        
        
        .cart-modal { background: white; border-radius: 20px; padding: 20px; max-width: 600px; width: 90%; max-height: 80vh; overflow-y: auto; position: relative; }
        .cart-item { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; padding: 10px; border-bottom: 1px solid #eee; }
        .cart-total { font-weight: bold; font-size: 1.2em; margin-top: 20px; text-align: center; }
        .checkout-btn { background: #e74c3c; color: white; border: none; padding: 15px; border-radius: 10px; cursor: pointer; width: 100%; margin-top: 20px; transition: background 0.3s; }
        .checkout-btn:hover:not(:disabled) { background: #c0392b; }
        .checkout-btn:disabled { background: #ccc; cursor: not-allowed; }
        .empty-cart { text-align: center; color: #666; font-style: italic; font-size: 1.2em; }
        .empty-cart::before { content: "🛒"; font-size: 2em; display: block; margin-bottom: 10px; }
        
       
        .checkout-form { display: none; margin-top: 20px; }
        .checkout-form.show { display: block; }
        .checkout-form input, .checkout-form select { width: 100%; padding: 10px; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 5px; }
        .pay-btn { background: #27ae60; color: white; border: none; padding: 15px; border-radius: 10px; cursor: pointer; width: 100%; }
        .pay-btn:hover { background: #229954; }
        
        
        @media (max-width: 768px) { 
            h1 { font-size: 2em; } 
            .grid { grid-template-columns: 1fr; } 
            .filters { flex-direction: column; align-items: center; } 
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Cloudy Bliss Bakery</h1>
            <p class="tagline">Order now! Phone: 7339651100. Enjoy cakes and cupcakes.</p>
            <div class="scrolling-discount"><span>10% off birthday cakes! 10% off birthday cakes! 10% off birthday cakes!</span></div>
            <div class="filters">
                <button id="allBtn" class="active">All</button>
                <button id="cakeBtn">Cakes</button>
                <button id="cupcakeBtn">Cupcakes</button>
            </div>
            <div class="cart-info" id="cartBtn">Cart: <span id="cartCount">0</span> items</div>
        </header>
        <div class="grid" id="dessertGrid"></div>
    </div>

    
    <div class="overlay" id="overlay">
        <div class="popup">
            <span class="close" id="closeBtn">&times;</span>
            <img id="popupImg" src="" alt="">
            <h2 id="popupTitle"></h2>
            <p id="popupDesc"></p>
            <p class="price" id="popupPrice"></p>
            <button class="add-btn" id="addBtn">Add to Cart</button>
        </div>
    </div>

   
    <div class="overlay" id="cartOverlay">
        <div class="cart-modal">
            <span class="close" id="cartCloseBtn">&times;</span>
            <h2>Your Cart</h2>
            <div id="cartItems"></div>
            <div class="cart-total">Total: $<span id="cartTotal">0.00</span></div>
            <button class="checkout-btn" id="checkoutBtn">Proceed to Checkout</button>
            <div class="checkout-form" id="checkoutForm">
                <h3>Checkout Details</h3>
                <input type="text" placeholder="Full Name" id="name">
                <input type="text" placeholder="Address" id="address">
                <select id="paymentMethod">
                    <option value="">Select Payment Method</option>
                    <option value="card">Credit Card</option>
                    <option value="paypal">PayPal</option>
                    <option value="cash">Cash on Delivery</option>
                </select>
                <button class="pay-btn" id="payBtn">Pay Now</button>
            </div>
        </div>
    </div>

    <script>
      
        const desserts = [
            { id: 1, name: "Creamy Cupcake Delight", type: "Cupcake", price: 5.45, desc: "Rich creamy cupcake with walnuts.", img: "https://images.unsplash.com/photo-1607478900766-efe13248b125?w=300&h=200&fit=crop" },
            { id: 2, name: "Birthday Cake", type: "Cake", price: 28.98, desc: "Vanilla cake with sprinkles.", img: "https://images.unsplash.com/photo-1535254973040-607b474cb50d?w=300&h=200&fit=crop" },
            { id: 3, name: "Black Forest Dream", type: "Cake", price: 33.49, desc: "Chocolate cake with cherries.", img: "https://www.fnp.com/images/pr/x/v20250612185112/blackforest-cake-1kg_1.jpg" },
            { id: 4, name: "Red Velvet", type: "Cake", price: 31.92, desc: "Red cake with frosting.", img: "https://thescranline.com/wp-content/uploads/2023/06/RED-VELVET-CAKE-23-S-01.jpg" },
            { id: 5, name: "Nutty Cupcake Bites", type: "Cupcake", price: 6.27, desc: "Mini cupcakes with pecans.", img: "https://images.unsplash.com/photo-1587668178277-295251f900ce?w=300&h=200&fit=crop" },
            { id: 6, name: "Strawberry Shortcake Surprise", type: "Cake", price: 26.94, desc: "Strawberries on sponge cake.", img: "https://rms-media-prod.generalmills.com/c9645ef5-d3ab-42c0-a734-d77a19fb539a.jpg" },
        ];

        let cart = [];
        const grid = document.getElementById('dessertGrid');
        const overlay = document.getElementById('overlay');
        const cartOverlay = document.getElementById('cartOverlay');
        const popupImg = document.getElementById('popupImg');
        const popupTitle = document.getElementById('popupTitle');
        const popupDesc = document.getElementById('popupDesc');
        const popupPrice = document.getElementById('popupPrice');
        const addBtn = document.getElementById('addBtn');
        const closeBtn = document.getElementById('closeBtn');
        const cartBtn = document.getElementById('cartBtn');
        const cartCloseBtn = document.getElementById('cartCloseBtn');
        const cartItems = document.getElementById('cartItems');
        const cartTotal = document.getElementById('cartTotal');
        const cartCount = document.getElementById('cartCount');
        const checkoutBtn = document.getElementById('checkoutBtn');
        const checkoutForm = document.getElementById('checkoutForm');
        const payBtn = document.getElementById('payBtn');
        const allBtn = document.getElementById('allBtn');
        const cakeBtn = document.getElementById('cakeBtn');
        const cupcakeBtn = document.getElementById('cupcakeBtn');

        
        function renderDesserts(filtered) {
            grid.innerHTML = '';
            filtered.forEach(d => {
                const card = document.createElement('div');
                card.className = 'card';
                card.onclick = () => openPopup(d);
                card.innerHTML = `
                    <img src="${d.img}" alt="${d.name}">
                    <h3>${d.name}</h3>
                    <p class="type">${d.type}</p>
                    <p class="price">$${d.price}</p>
                `;
                grid.appendChild(card);
            });
        }

        
        function openPopup(dessert) {
            popupImg.src = dessert.img;
            popupTitle.textContent = dessert.name;
            popupDesc.textContent = dessert.desc;
            popupPrice.textContent = `$${dessert.price}`;
            addBtn.onclick = () => addToCart(dessert);
            overlay.classList.add('show');
        }

        closeBtn.onclick = () => overlay.classList.remove('show');
        overlay.onclick = (e) => { if (e.target === overlay) overlay.classList.remove('show'); };
        cartCloseBtn.onclick = () => cartOverlay.classList.remove('show');
        cartOverlay.onclick = (e) => { if (e.target === cartOverlay) cartOverlay.classList.remove('show'); };

        
        function addToCart(dessert) {
            cart.push(dessert);
            updateCart();
            overlay.classList.remove('show');
        }

       
        function updateCart() {
            cartItems.innerHTML = '';
            let total = 0;
            if (cart.length === 0) {
                cartItems.innerHTML = '<p class="empty-cart">Oops, no items added</p>';
                checkoutBtn.disabled = true;
                checkoutBtn.style.display = 'none';
                document.querySelector('.cart-total').style.display = 'none';
            } else {
                cart.forEach(item => {
                    total += item.price;
                    const itemDiv = document.createElement('div');
                    itemDiv.className = 'cart-item';
                    itemDiv.innerHTML = `<span>${item.name}</span><span>$${item.price}</span>`;
                    cartItems.appendChild(itemDiv);
                });
                checkoutBtn.disabled = false;
                checkoutBtn.style.display = 'block';
                document.querySelector('.cart-total').style.display = 'block';
            }
            cartTotal.textContent = total.toFixed(2);
            cartCount.textContent = cart.length;
        }

        
        cartBtn.onclick = () => {
            updateCart();
            cartOverlay.classList.add('show');
        };

        
        checkoutBtn.onclick = () => {
            if (cart.length === 0) {
                alert('Your cart is empty! Add some delicious treats first. 🍰');
                return;
            }
            checkoutForm.classList.add('show');
        };

        
        payBtn.onclick = () => {
            const name = document.getElementById('name').value;
            const address = document.getElementById('address').value;
            const payment = document.getElementById('paymentMethod').value;
            if (!name || !address || !payment) {
                alert('Please fill in all fields!');
                return;
            }
            alert(`Order placed! Thanks ${name}, your desserts are on the way to ${address} via ${payment}.`);
            cart = [];
            updateCart();
            cartOverlay.classList.remove('show');
            checkoutForm.classList.remove('show');
        };

       
        allBtn.onclick = () => { renderDesserts(desserts); setActive(allBtn); };
        cakeBtn.onclick = () => { renderDesserts(desserts.filter(d => d.type === 'Cake')); setActive(cakeBtn); };
        cupcakeBtn.onclick = () => { renderDesserts(desserts.filter(d => d.type === 'Cupcake')); setActive(cupcakeBtn); };

        function setActive(btn) {
            [allBtn, cakeBtn, cupcakeBtn].forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
        }

        
        renderDesserts(desserts);
    </script>
</body>
</html>
