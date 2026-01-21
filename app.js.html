// ====== CONFIG ======
const WHATSAPP_NUMBER = "8801XXXXXXXXX"; // <- replace with your number (no +, no spaces)
// Example: "8801958424010"

const PRODUCTS = [
  {
    id: "bag-001",
    name: "Elegant Office Handbag",
    price: 1850,
    desc: "Premium finish, spacious compartments, perfect for office and daily use.",
    placeholder: "OFFICE"
  },
  {
    id: "bag-002",
    name: "Casual Crossbody Bag",
    price: 1450,
    desc: "Lightweight and stylish, ideal for shopping and casual outings.",
    placeholder: "CASUAL"
  },
  {
    id: "bag-003",
    name: "Luxury Party Handbag",
    price: 2250,
    desc: "Elegant look for parties and events. Durable zipper and premium build.",
    placeholder: "PARTY"
  },
  {
    id: "bag-004",
    name: "Travel Tote Bag",
    price: 1990,
    desc: "Large capacity tote for travel and everyday essentials.",
    placeholder: "TOTE"
  },
  {
    id: "bag-005",
    name: "Mini Shoulder Bag",
    price: 1190,
    desc: "Compact and trendy. Best for quick carry and minimal essentials.",
    placeholder: "MINI"
  }
];

// ====== STATE ======
const CART_KEY = "lunabag_cart_v1";

function loadCart() {
  try {
    const raw = localStorage.getItem(CART_KEY);
    return raw ? JSON.parse(raw) : {};
  } catch {
    return {};
  }
}

function saveCart(cart) {
  localStorage.setItem(CART_KEY, JSON.stringify(cart));
}

function cartCount(cart) {
  return Object.values(cart).reduce((sum, qty) => sum + qty, 0);
}

function cartTotal(cart) {
  let total = 0;
  for (const [id, qty] of Object.entries(cart)) {
    const p = PRODUCTS.find(x => x.id === id);
    if (p) total += p.price * qty;
  }
  return total;
}

function formatBDT(n) {
  return "৳" + n.toLocaleString("en-US");
}

function buildOrderText(cart, customer) {
  const lines = [];
  lines.push("New Order — LunaBag");
  lines.push("----------------------------");
  lines.push(`Name: ${customer.name}`);
  lines.push(`Phone: ${customer.phone}`);
  lines.push(`Address: ${customer.address}`);
  lines.push(`Payment: ${customer.payment}`);
  if (customer.note) lines.push(`Note: ${customer.note}`);
  lines.push("");
  lines.push("Items:");
  for (const [id, qty] of Object.entries(cart)) {
    const p = PRODUCTS.find(x => x.id === id);
    if (!p) continue;
    lines.push(`- ${p.name} x${qty} = ${formatBDT(p.price * qty)}`);
  }
  lines.push("");
  lines.push(`Total: ${formatBDT(cartTotal(cart))}`);
  lines.push("----------------------------");
  lines.push("Please confirm availability & delivery time.");
  return lines.join("\n");
}

function openWhatsApp(message) {
  const encoded = encodeURIComponent(message);
  const url = `https://wa.me/${WHATSAPP_NUMBER}?text=${encoded}`;
  window.open(url, "_blank");
}

// ====== UI ======
const productGrid = document.getElementById("productGrid");
const cartCountEl = document.getElementById("cartCount");
const cartDrawer = document.getElementById("cartDrawer");
const cartItemsEl = document.getElementById("cartItems");
const cartTotalEl = document.getElementById("cartTotal");

const openCartBtn = document.getElementById("openCartBtn");
const closeCartBtn = document.getElementById("closeCartBtn");
const closeCartOverlay = document.getElementById("closeCartOverlay");

const clearCartBtn = document.getElementById("clearCartBtn");
const goCheckoutBtn = document.getElementById("goCheckoutBtn");

const checkoutModal = document.getElementById("checkoutModal");
const openCheckoutBtn = document.getElementById("openCheckoutBtn");
const closeCheckoutBtn = document.getElementById("closeCheckoutBtn");
const closeCheckoutOverlay = document.getElementById("closeCheckoutOverlay");
const checkoutSummary = document.getElementById("checkoutSummary");
const checkoutForm = document.getElementById("checkoutForm");
const copyOrderBtn = document.getElementById("copyOrderBtn");
const whatsAppOrderBtn = document.getElementById("whatsAppOrderBtn");

const searchInput = document.getElementById("searchInput");
const sortSelect = document.getElementById("sortSelect");

document.getElementById("year").textContent = new Date().getFullYear();
document.getElementById("whatsNumberText").textContent = "+" + WHATSAPP_NUMBER;

let cart = loadCart();

function setCartBadge() {
  cartCountEl.textContent = String(cartCount(cart));
}

function renderProducts(list) {
  productGrid.innerHTML = "";
  list.forEach(p => {
    const qty = cart[p.id] || 0;

    const el = document.createElement("div");
    el.className = "product";
    el.innerHTML = `
      <div class="product__img">${p.placeholder}</div>
      <div class="product__body">
        <div class="product__title">${p.name}</div>
        <div class="product__desc">${p.desc}</div>
        <div class="product__row">
          <div class="price">${formatBDT(p.price)}</div>
          <div class="qtyRow">
            <button class="qtyBtn" data-act="dec" data-id="${p.id}">−</button>
            <span class="small" data-qty="${p.id}">${qty}</span>
            <button class="qtyBtn" data-act="inc" data-id="${p.id}">+</button>
          </div>
        </div>
        <button class="btn" data-act="add" data-id="${p.id}">Add to Cart</button>
      </div>
    `;
    productGrid.appendChild(el);
  });
}

function renderCart() {
  cartItemsEl.innerHTML = "";
  const entries = Object.entries(cart);

  if (entries.length === 0) {
    cartItemsEl.innerHTML = `<div class="muted">Your cart is empty.</div>`;
    cartTotalEl.textContent = formatBDT(0);
    return;
  }

  for (const [id, qty] of entries) {
    const p = PRODUCTS.find(x => x.id === id);
    if (!p) continue;

    const row = document.createElement("div");
    row.className = "cartItem";
    row.innerHTML = `
      <div class="cartItem__thumb">${p.placeholder}</div>
      <div class="cartItem__info">
        <div class="cartItem__title">${p.name}</div>
        <div class="cartItem__meta">
          <span>${formatBDT(p.price)} each</span>
          <span><strong>${formatBDT(p.price * qty)}</strong></span>
        </div>
        <div class="cartItem__actions">
          <button class="qtyBtn" data-cart="dec" data-id="${p.id}">−</button>
          <button class="qtyBtn" data-cart="inc" data-id="${p.id}">+</button>
          <button class="qtyBtn" data-cart="remove" data-id="${p.id}" title="Remove">✕</button>
        </div>
      </div>
    `;
    cartItemsEl.appendChild(row);
  }

  cartTotalEl.textContent = formatBDT(cartTotal(cart));
}

function openCart() {
  cartDrawer.classList.add("isOpen");
  cartDrawer.setAttribute("aria-hidden", "false");
  renderCart();
}

function closeCart() {
  cartDrawer.classList.remove("isOpen");
  cartDrawer.setAttribute("aria-hidden", "true");
}

function openCheckout() {
  checkoutModal.classList.add("isOpen");
  checkoutModal.setAttribute("aria-hidden", "false");

  if (cartCount(cart) === 0) {
    checkoutSummary.textContent = "Your cart is empty. Please add products before checkout.";
    return;
  }

  const lines = [];
  for (const [id, qty] of Object.entries(cart)) {
    const p = PRODUCTS.find(x => x.id === id);
    if (!p) continue;
    lines.push(`${p.name} x${qty} = ${formatBDT(p.price * qty)}`);
  }
  checkoutSummary.innerHTML = `
    <div><strong>Order Summary</strong></div>
    <div style="margin-top:6px">${lines.join("<br/>")}</div>
    <div style="margin-top:8px"><strong>Total: ${formatBDT(cartTotal(cart))}</strong></div>
  `;
}

function closeCheckout() {
  checkoutModal.classList.remove("isOpen");
  checkoutModal.setAttribute("aria-hidden", "true");
}

// Product actions
productGrid.addEventListener("click", (e) => {
  const btn = e.target.closest("button");
  if (!btn) return;

  const id = btn.getAttribute("data-id");
  const act = btn.getAttribute("data-act");
  if (!id || !act) return;

  if (act === "add" || act === "inc") {
    cart[id] = (cart[id] || 0) + 1;
  } else if (act === "dec") {
    cart[id] = Math.max(0, (cart[id] || 0) - 1);
    if (cart[id] === 0) delete cart[id];
  }

  saveCart(cart);
  setCartBadge();
  refreshProducts();
});

cartItemsEl.addEventListener("click", (e) => {
  const btn = e.target.closest("button");
  if (!btn) return;

  const id = btn.getAttribute("data-id");
  const action = btn.getAttribute("data-cart");
  if (!id || !action) return;

  if (action === "inc") cart[id] = (cart[id] || 0) + 1;
  if (action === "dec") {
    cart[id] = Math.max(0, (cart[id] || 0) - 1);
    if (cart[id] === 0) delete cart[id];
  }
  if (action === "remove") delete cart[id];

  saveCart(cart);
  setCartBadge();
  renderCart();
  refreshProducts();
});

// Drawer / modal controls
openCartBtn.addEventListener("click", openCart);
closeCartBtn.addEventListener("click", closeCart);
closeCartOverlay.addEventListener("click", closeCart);

openCheckoutBtn.addEventListener("click", () => {
  openCheckout();
});
document.getElementById("goCheckoutBtn").addEventListener("click", () => {
  closeCart();
  openCheckout();
});

closeCheckoutBtn.addEventListener("click", closeCheckout);
closeCheckoutOverlay.addEventListener("click", closeCheckout);

clearCartBtn.addEventListener("click", () => {
  cart = {};
  saveCart(cart);
  setCartBadge();
  renderCart();
  refreshProducts();
});

whatsAppOrderBtn.addEventListener("click", () => {
  if (cartCount(cart) === 0) {
    alert("Your cart is empty.");
    return;
  }
  const msg = buildOrderText(cart, {
    name: "Customer",
    phone: "01XXXXXXXXX",
    address: "Address",
    payment: "Cash on Delivery",
    note: ""
  });
  openWhatsApp(msg);
});

// Search & sort
function refreshProducts() {
  const q = (searchInput.value || "").trim().toLowerCase();
  let list = [...PRODUCTS].filter(p =>
    p.name.toLowerCase().includes(q) || p.desc.toLowerCase().includes(q)
  );

  const sort = sortSelect.value;
  if (sort === "priceAsc") list.sort((a,b) => a.price - b.price);
  if (sort === "priceDesc") list.sort((a,b) => b.price - a.price);
  if (sort === "nameAsc") list.sort((a,b) => a.name.localeCompare(b.name));
  // featured = default order

  renderProducts(list);
}

searchInput.addEventListener("input", refreshProducts);
sortSelect.addEventListener("change", refreshProducts);

// Checkout form -> WhatsApp
checkoutForm.addEventListener("submit", (e) => {
  e.preventDefault();
  if (cartCount(cart) === 0) {
    alert("Your cart is empty.");
    return;
  }

  const formData = new FormData(checkoutForm);
  const customer = {
    name: String(formData.get("name") || "").trim(),
    phone: String(formData.get("phone") || "").trim(),
    address: String(formData.get("address") || "").trim(),
    payment: String(formData.get("payment") || "").trim(),
    note: String(formData.get("note") || "").trim()
  };

  const msg = buildOrderText(cart, customer);
  openWhatsApp(msg);

  // optional: clear cart after sending
  cart = {};
  saveCart(cart);
  setCartBadge();
  refreshProducts();
  closeCheckout();
});

copyOrderBtn.addEventListener("click", async () => {
  if (cartCount(cart) === 0) {
    alert("Your cart is empty.");
    return;
  }
  // Use placeholder customer fields (user can edit in WhatsApp)
  const msg = buildOrderText(cart, {
    name: "Customer",
    phone: "01XXXXXXXXX",
    address: "Address",
    payment: "Cash on Delivery",
    note: ""
  });

  try {
    await navigator.clipboard.writeText(msg);
    alert("Order text copied!");
  } catch {
    alert("Copy failed. Please try again.");
  }
});

// Init
setCartBadge();
refreshProducts();
