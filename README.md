cat > /mnt/user-data/outputs/index.html << 'EOF'
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>سلة الدار</title>
<style>
* { margin:0; padding:0; box-sizing:border-box; }
body { font-family: 'Segoe UI', Tahoma, Arial, sans-serif; background:#f4f6f4; direction:rtl; }
.screen { display:none; min-height:100vh; }
.screen.active { display:block; }
.btn { cursor:pointer; font-family:inherit; border:none; }
.header { background:#1e7d34; padding:18px 16px; display:flex; align-items:center; gap:12px; }
.header h2 { color:#fff; font-size:18px; font-weight:800; }
.back { background:none; border:none; color:#fff; font-size:22px; cursor:pointer; }

/* HOME */
#home { background:linear-gradient(160deg,#0f2d16,#1e7d34 60%,#2ecc52); display:flex; flex-direction:column; align-items:center; justify-content:center; padding:32px 24px; }
.logo { font-size:72px; margin-bottom:8px; text-align:center; }
.logo-title { color:#fff; font-size:40px; font-weight:900; text-align:center; }
.logo-sub { color:#a7f3c0; font-size:15px; text-align:center; margin-top:8px; margin-bottom:24px; }
.cats { display:flex; flex-wrap:wrap; gap:8px; justify-content:center; margin-bottom:32px; }
.cat-badge { background:rgba(255,255,255,0.15); color:#fff; border-radius:20px; padding:4px 12px; font-size:13px; }
.menu { display:grid; gap:12px; width:100%; max-width:360px; }
.menu-btn { border-radius:14px; padding:16px 20px; font-size:16px; font-weight:700; text-align:right; box-shadow:0 4px 20px rgba(0,0,0,0.2); cursor:pointer; border:none; }
.sub-note { color:#6ee7a0; font-size:13px; margin-top:20px; text-align:center; }

/* REGISTER */
.reg-body { padding:20px; }
.field { margin-bottom:16px; }
.field label { display:block; color:#145a24; font-weight:700; margin-bottom:6px; font-size:14px; }
.field input { width:100%; padding:13px 14px; border-radius:10px; border:1.5px solid #d1fae5; font-size:15px; background:#fff; direction:rtl; outline:none; font-family:inherit; }
.sub-box { background:#fff7ed; border:1.5px solid #fed7aa; border-radius:12px; padding:14px; margin-bottom:16px; }
.sub-box p { color:#92400e; font-weight:700; font-size:14px; }
.sub-box span { color:#b45309; font-size:13px; }
.green-btn { width:100%; background:#1e7d34; color:#fff; border:none; border-radius:12px; padding:16px; font-size:17px; font-weight:800; cursor:pointer; font-family:inherit; }
.success { padding:32px; text-align:center; }
.success .icon { font-size:64px; margin-bottom:12px; }
.success h2 { color:#1e7d34; font-size:24px; font-weight:800; margin-bottom:16px; }
.pay-box { background:#fff; border-radius:14px; padding:16px; margin:16px 0; border:2px solid #2ecc52; }
.pay-amount { background:#1e7d34; color:#fff; border-radius:10px; padding:10px 16px; font-weight:700; font-size:18px; margin-top:8px; text-align:center; }

/* SHOP */
.shop-header { background:#1e7d34; padding:16px 16px 0; }
.shop-top { display:flex; justify-content:space-between; align-items:center; margin-bottom:12px; }
.shop-title { color:#fff; font-weight:800; font-size:18px; }
.shop-sub { color:#a7f3c0; font-size:12px; }
.cart-btn { background:rgba(255,255,255,0.2); border:none; border-radius:12px; padding:8px 14px; color:#fff; font-weight:700; font-size:15px; cursor:pointer; }
.cart-btn.has-items { background:#ff6b35; }
.cats-scroll { display:flex; gap:8px; overflow-x:auto; padding-bottom:12px; }
.cats-scroll::-webkit-scrollbar { display:none; }
.cat-btn { background:rgba(255,255,255,0.15); color:#fff; border:none; border-radius:20px; padding:6px 14px; font-size:13px; font-weight:600; white-space:nowrap; flex-shrink:0; cursor:pointer; font-family:inherit; }
.cat-btn.active { background:#fff; color:#1e7d34; }
.products { display:grid; grid-template-columns:1fr 1fr; gap:12px; padding:16px; }
.product-card { background:#fff; border-radius:14px; padding:14px; box-shadow:0 2px 8px rgba(0,0,0,0.06); }
.product-emoji { font-size:40px; text-align:center; margin-bottom:8px; }
.product-name { font-weight:700; font-size:14px; margin-bottom:2px; }
.product-seller { color:#6b7280; font-size:11px; margin-bottom:6px; }
.product-row { display:flex; justify-content:space-between; align-items:center; }
.product-price { color:#1e7d34; font-weight:800; font-size:15px; }
.add-btn { background:#1e7d34; color:#fff; border:none; border-radius:8px; padding:5px 10px; font-size:13px; font-weight:700; cursor:pointer; }
.product-rating { color:#f59e0b; font-size:12px; margin-top:4px; }
.cart-float { position:fixed; bottom:20px; left:16px; right:16px; background:#1e7d34; color:#fff; border:none; border-radius:14px; padding:16px; font-size:16px; font-weight:800; cursor:pointer; box-shadow:0 6px 20px rgba(30,125,52,0.4); font-family:inherit; }

/* CART */
.cart-items { padding:16px; }
.cart-item { background:#fff; border-radius:14px; padding:14px; margin-bottom:10px; display:flex; justify-content:space-between; align-items:center; }
.item-info .emoji { font-size:28px; }
.item-info .name { font-weight:700; font-size:14px; }
.item-info .price { color:#1e7d34; font-weight:700; }
.remove-btn { background:#fee2e2; color:#dc2626; border:none; border-radius:8px; padding:6px 12px; font-weight:700; cursor:pointer; }
.cart-total { background:#fff; border-radius:14px; padding:16px; margin-top:8px; }
.total-row { display:flex; justify-content:space-between; margin-bottom:12px; }
.total-label { color:#6b7280; }
.total-amount { font-weight:800; color:#1e7d34; font-size:18px; }
.empty-cart { padding:40px; text-align:center; }
.empty-cart .icon { font-size:60px; }
.empty-cart p { color:#6b7280; font-size:16px; margin:12px 0; }
.order-success { padding:32px; text-align:center; }
.order-success .icon { font-size:72px; }
.order-success h2 { color:#1e7d34; font-weight:800; margin:12px 0; }

/* ADMIN */
#admin { background:#0f1f14; }
.admin-header { background:linear-gradient(135deg,#0f2d16,#1e7d34); padding:20px; }
.admin-top { display:flex; justify-content:space-between; align-items:center; margin-bottom:16px; }
.admin-title { color:#fff; font-weight:900; font-size:22px; }
.admin-sub { color:#4ade80; font-size:12px; font-weight:600; }
.exit-btn { background:rgba(255,255,255,0.1); border:none; color:#fff; border-radius:10px; padding:8px 14px; cursor:pointer; font-size:13px; }
.stats { display:grid; grid-template-columns:1fr 1fr; gap:10px; }
.stat-card { background:rgba(255,255,255,0.08); border-radius:14px; padding:14px; border:1px solid rgba(255,255,255,0.1); }
.stat-icon { font-size:24px; }
.stat-val { color:#4ade80; font-weight:900; font-size:18px; margin-top:4px; }
.stat-label { color:#86efac; font-size:12px; }
.admin-body { padding:16px; }
.section-title { color:#4ade80; font-weight:800; margin-bottom:12px; font-size:16px; }
.order-card { background:#1a3a24; border-radius:14px; padding:14px; margin-bottom:10px; border:1px solid rgba(74,222,128,0.15); display:flex; justify-content:space-between; align-items:flex-start; }
.order-id { color:#fff; font-weight:700; }
.order-info { color:#86efac; font-size:13px; margin-top:2px; }
.order-time { color:#6b7280; font-size:12px; margin-top:2px; }
.status-badge { border-radius:20px; padding:4px 10px; font-size:12px; font-weight:700; }
.coming { background:#1a2a3a; border-radius:14px; padding:16px; margin-top:16px; border:1px solid rgba(59,130,246,0.3); }
.coming-title { color:#60a5fa; font-weight:800; margin-bottom:10px; }
.coming-item { color:#93c5fd; font-size:14px; padding:6px 0; border-bottom:1px solid rgba(59,130,246,0.1); }
</style>
</head>
<body>

<!-- HOME -->
<div id="home" class="screen active">
  <div class="logo">🏠</div>
  <div class="logo-title">سلة الدار</div>
  <div class="logo-sub">كل ما تحتاجه لدارك... فخطوة وحدة</div>
  <div class="cats">
    <span class="cat-badge">🥬 خضرة</span>
    <span class="cat-badge">🥩 لحم</span>
    <span class="cat-badge">🐟 حوت</span>
    <span class="cat-badge">🧺 منزلية</span>
    <span class="cat-badge">🍳 مطبخ</span>
    <span class="cat-badge">🔌 أجهزة</span>
  </div>
  <div class="menu">
    <button class="menu-btn" style="background:#fff;color:#145a24" onclick="goRegister('client')">🛒 زبون — اطلب الآن</button>
    <button class="menu-btn" style="background:#2ecc52;color:#fff" onclick="goRegister('seller')">🏪 بائع — سجل متجرك</button>
    <button class="menu-btn" style="background:#1a3a24;color:#a7f3c0" onclick="goRegister('livreur')">🛵 ليفريور — انضم للفريق</button>
    <button class="menu-btn" style="background:#0f1a12;color:#4ade80" onclick="show('admin')">⚙️ لوحة التحكم</button>
  </div>
  <div class="sub-note">الاشتراك: 200 درهم / شهر للبائعين والليفريورات</div>
</div>

<!-- REGISTER -->
<div id="register" class="screen">
  <div class="header">
    <button class="back" onclick="show('home')">←</button>
    <div>
      <h2 id="reg-title">تسجيل</h2>
      <div id="reg-sub" style="color:#a7f3c0;font-size:12px;display:none">اشتراك شهري: 200 درهم</div>
    </div>
  </div>
  <div id="reg-form" class="reg-body">
    <div class="field"><label>الاسم الكامل</label><input type="text" placeholder="مثال: أحمد مرابط" id="f-name"></div>
    <div class="field"><label>رقم الهاتف</label><input type="tel" placeholder="06xxxxxxxx" id="f-phone"></div>
    <div class="field"><label>المدينة</label><input type="text" placeholder="الدار البيضاء، الرباط..." id="f-city"></div>
    <div id="seller-field" class="field" style="display:none"><label>نوع المتجر</label><input type="text" placeholder="مثال: خضرة، لحم..." id="f-type"></div>
    <div id="sub-warning" class="sub-box" style="display:none">
      <p>💳 الاشتراك الشهري: 200 درهم</p>
      <span>يُدفع بعد تأكيد التسجيل من الإدارة</span>
    </div>
    <button class="green-btn" onclick="doRegister()">تسجيل الآن ✅</button>
  </div>
  <div id="reg-success" class="success" style="display:none">
    <div class="icon">✅</div>
    <h2>تم التسجيل بنجاح!</h2>
    <div id="pay-section" style="display:none">
      <div class="pay-box">
        <p style="font-weight:600">💳 ادفع اشتراكك الشهري</p>
        <div class="pay-amount">200 درهم / شهر</div>
      </div>
    </div>
    <button class="green-btn" id="after-reg-btn" onclick="afterRegister()">🛒 ابدأ التسوق</button>
  </div>
</div>

<!-- SHOP -->
<div id="shop" class="screen">
  <div class="shop-header">
    <div class="shop-top">
      <div><div class="shop-sub">مرحبًا 👋</div><div class="shop-title">سلة الدار</div></div>
      <button class="cart-btn" id="cart-btn" onclick="show('cart')">🛒</button>
    </div>
    <div class="cats-scroll">
      <button class="cat-btn active" onclick="filterCat('khodra',this)">🥬 خضرة وفواكه</button>
      <button class="cat-btn" onclick="filterCat('lahm',this)">🥩 لحم ودجاج</button>
      <button class="cat-btn" onclick="filterCat('hout',this)">🐟 حوت وسمك</button>
      <button class="cat-btn" onclick="filterCat('manzili',this)">🧺 مواد منزلية</button>
      <button class="cat-btn" onclick="filterCat('matbakh',this)">🍳 أدوات المطبخ</button>
      <button class="cat-btn" onclick="filterCat('ajhiza',this)">🔌 أجهزة منزلية</button>
    </div>
  </div>
  <div class="products" id="products-grid"></div>
  <button class="cart-float" id="cart-float" style="display:none" onclick="show('cart')"></button>
</div>

<!-- CART -->
<div id="cart" class="screen">
  <div class="header">
    <button class="back" onclick="show('shop')">←</button>
    <h2>🛒 سلتك</h2>
  </div>
  <div id="cart-content"></div>
</div>

<!-- ADMIN -->
<div id="admin" class="screen">
  <div class="admin-header">
    <div class="admin-top">
      <div><div class="admin-sub">لوحة التحكم</div><div class="admin-title">🏠 سلة الدار</div></div>
      <button class="exit-btn" onclick="show('home')">خروج</button>
    </div>
    <div class="stats">
      <div class="stat-card"><div class="stat-icon">📦</div><div class="stat-val">1,042</div><div class="stat-label">إجمالي الطلبات</div></div>
      <div class="stat-card"><div class="stat-icon">🏪</div><div class="stat-val">3</div><div class="stat-label">البائعون النشطون</div></div>
      <div class="stat-card"><div class="stat-icon">🛵</div><div class="stat-val">8</div><div class="stat-label">الليفريورات</div></div>
      <div class="stat-card"><div class="stat-icon">💰</div><div class="stat-val">1,200 د</div><div class="stat-label">الدخل/شهر</div></div>
    </div>
  </div>
  <div class="admin-body">
    <div class="section-title">📦 آخر الطلبات</div>
    <div class="order-card">
      <div><div class="order-id">#1042 — أحمد مرابط</div><div class="order-info">3 منتجات • 87 درهم</div><div class="order-time">🛵 يوسف • منذ 12 دقيقة</div></div>
      <span class="status-badge" style="background:#f59e0b22;color:#f59e0b;border:1px solid #f59e0b44">قيد التوصيل</span>
    </div>
    <div class="order-card">
      <div><div class="order-id">#1041 — فاطمة الزهراء</div><div class="order-info">5 منتجات • 156 درهم</div><div class="order-time">🛵 كريم • منذ 1 ساعة</div></div>
      <span class="status-badge" style="background:#1e7d3422;color:#1e7d34;border:1px solid #1e7d3444">تم التوصيل</span>
    </div>
    <div class="order-card">
      <div><div class="order-id">#1040 — محمد العلوي</div><div class="order-info">2 منتجات • 45 درهم</div><div class="order-time">🛵 — • منذ 5 دقائق</div></div>
      <span class="status-badge" style="background:#3b82f622;color:#3b82f6;border:1px solid #3b82f644">جديد</span>
    </div>
    <div class="coming">
      <div class="coming-title">⏳ قريبًا</div>
      <div class="coming-item">📍 تتبع GPS مباشر</div>
      <div class="coming-item">💳 دفع إلكتروني متطور</div>
      <div class="coming-item">📢 نظام إعلانات</div>
      <div class="coming-item">🤖 ذكاء اصطناعي</div>
    </div>
  </div>
</div>

<script>
const products = [
  { id:1, name:"طماطم طازجة", price:4, unit:"كيلو", cat:"khodra", seller:"فرم البركة", rating:4.8, img:"🍅" },
  { id:2, name:"دجاج بلدي", price:28, unit:"كيلو", cat:"lahm", seller:"الجزارة الذهبية", rating:4.9, img:"🍗" },
  { id:3, name:"سمك سردين", price:15, unit:"كيلو", cat:"hout", seller:"سوق البحر", rating:4.7, img:"🐟" },
  { id:4, name:"بطاطس", price:3, unit:"كيلو", cat:"khodra", seller:"فرم البركة", rating:4.6, img:"🥔" },
  { id:5, name:"لحم بقري", price:90, unit:"كيلو", cat:"lahm", seller:"الجزارة الذهبية", rating:4.9, img:"🥩" },
  { id:6, name:"مسحوق غسيل", price:35, unit:"قطعة", cat:"manzili", seller:"بيت النظافة", rating:4.5, img:"🧴" },
  { id:7, name:"خلاط كهربائي", price:250, unit:"قطعة", cat:"ajhiza", seller:"إلكترو دار", rating:4.8, img:"🥤" },
  { id:8, name:"طاجين", price:80, unit:"قطعة", cat:"matbakh", seller:"فخار الأطلس", rating:4.7, img:"🫕" },
];

let cart = [];
let currentRole = 'client';
let currentCat = 'khodra';

function show(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  if(id === 'shop') renderProducts();
  if(id === 'cart') renderCart();
}

function goRegister(role) {
  currentRole = role;
  document.getElementById('reg-title').textContent = role==='client'?'تسجيل زبون':role==='seller'?'تسجيل بائع':'تسجيل ليفريور';
  document.getElementById('reg-sub').style.display = (role!=='client')?'block':'none';
  document.getElementById('seller-field').style.display = (role==='seller')?'block':'none';
  document.getElementById('sub-warning').style.display = (role!=='client')?'block':'none';
  document.getElementById('reg-form').style.display = 'block';
  document.getElementById('reg-success').style.display = 'none';
  show('register');
}

function doRegister() {
  document.getElementById('reg-form').style.display = 'none';
  document.getElementById('reg-success').style.display = 'block';
  document.getElementById('pay-section').style.display = (currentRole!=='client')?'block':'none';
  const btn = document.getElementById('after-reg-btn');
  btn.textContent = currentRole==='client'?'🛒 ابدأ التسوق':'العودة للرئيسية';
}

function afterRegister() {
  if(currentRole==='client') show('shop');
  else show('home');
}

function filterCat(cat, btn) {
  currentCat = cat;
  document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderProducts();
}

function renderProducts() {
  const grid = document.getElementById('products-grid');
  const filtered = products.filter(p => p.cat === currentCat);
  if(filtered.length === 0) {
    grid.innerHTML = '<div style="grid-column:1/-1;text-align:center;color:#6b7280;padding:40px"><div style="font-size:40px">📦</div><p>لا توجد منتجات حاليًا</p></div>';
    return;
  }
  grid.innerHTML = filtered.map(p => `
    <div class="product-card">
      <div class="product-emoji">${p.img}</div>
      <div class="product-name">${p.name}</div>
      <div class="product-seller">من: ${p.seller}</div>
      <div class="product-row">
        <span class="product-price">${p.price} د/${p.unit}</span>
        <button class="add-btn" onclick="addToCart(${p.id})">+ أضف</button>
      </div>
      <div class="product-rating">⭐ ${p.rating}</div>
    </div>
  `).join('');
  updateCartBtn();
}

function addToCart(id) {
  const p = products.find(p => p.id === id);
  const ex = cart.find(i => i.id === id);
  if(ex) ex.qty++;
  else cart.push({...p, qty:1});
  updateCartBtn();
}

function updateCartBtn() {
  const count = cart.reduce((s,i)=>s+i.qty,0);
  const total = cart.reduce((s,i)=>s+i.price*i.qty,0);
  const btn = document.getElementById('cart-btn');
  const float = document.getElementById('cart-float');
  btn.textContent = count>0?`🛒 ${count}`:'🛒';
  btn.className = count>0?'cart-btn has-items':'cart-btn';
  if(count>0) { float.style.display='block'; float.textContent=`🛒 السلة (${count}) — ${total} درهم`; }
  else float.style.display='none';
}

function removeFromCart(id) {
  cart = cart.filter(i=>i.id!==id);
  renderCart();
  updateCartBtn();
}

function renderCart() {
  const content = document.getElementById('cart-content');
  if(cart.length===0) {
    content.innerHTML = '<div class="empty-cart"><div class="icon">🛒</div><p>سلتك فارغة</p><button class="green-btn" style="width:auto;padding:12px 24px" onclick="show(\'shop\')">تسوق الآن</button></div>';
    return;
  }
  const total = cart.reduce((s,i)=>s+i.price*i.qty,0);
  content.innerHTML = `
    <div class="cart-items">
      ${cart.map(i=>`
        <div class="cart-item">
          <div class="item-info">
            <div class="emoji">${i.img}</div>
            <div class="name">${i.name}</div>
            <div class="price">${i.price*i.qty} درهم × ${i.qty}</div>
          </div>
          <button class="remove-btn" onclick="removeFromCart(${i.id})">حذف</button>
        </div>
      `).join('')}
      <div class="cart-total">
        <div class="total-row"><span class="total-label">المجموع</span><span class="total-amount">${total} درهم</span></div>
        <button class="green-btn" onclick="placeOrder()">✅ تأكيد الطلب — الدفع عند الاستلام</button>
      </div>
    </div>
  `;
}

function placeOrder() {
  cart = [];
  updateCartBtn();
  document.getElementById('cart-content').innerHTML = `
    <div class="order-success">
      <div class="icon">🎉</div>
      <h2>تم إرسال طلبك!</h2>
      <p style="color:#6b7280">الليفريور في طريقه إليك 🛵</p>
      <button class="green-btn" style="margin-top:20px" onclick="show('shop')">العودة للتسوق</button>
    </div>
  `;
}

renderProducts();
</script>
</body>
</html>
EOF
echo "Done
