<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
  <title>Madame Ganja Headshop — MVP 9:16</title>
  <style>
    :root {
      --bg:#0b0b0b; --fg:#f1f1f1; --muted:#a9a9a9; --accent:#25d366; --card:#141414; --line:#222; --danger:#ff5555;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:var(--bg);color:var(--fg);font-family:system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Inter,Helvetica,Arial,sans-serif}
    /* 9:16 phone frame */
    .phone{
      width:360px; height:640px; /* 9:16 */
      margin:24px auto; background:var(--card); border:1px solid var(--line); border-radius:28px; box-shadow:0 10px 30px rgba(0,0,0,.45); overflow:hidden; position:relative
    }
    .statusbar{height:28px; display:flex; align-items:center; justify-content:flex-end; padding:0 10px; gap:8px; font-size:12px; color:var(--muted); background:#0f0f0f; border-bottom:1px solid var(--line)}
    .appbar{height:48px; display:flex; align-items:center; justify-content:space-between; padding:0 12px; border-bottom:1px solid var(--line); background:#0f0f0f}
    .logo{font-weight:700; letter-spacing:.3px}
    .pill{display:inline-flex; align-items:center; gap:6px; background:#121212; border:1px solid var(--line); padding:6px 10px; border-radius:999px; font-size:12px; color:var(--muted)}
    .screen{position:absolute; inset:28px 0 0 0; display:none; overflow:auto; -webkit-overflow-scrolling:touch}
    .active{display:block}
    .content{padding:12px}
    .banner{height:140px; border:1px dashed var(--line); border-radius:16px; display:flex; align-items:center; justify-content:center; color:var(--muted)}
    .categories{display:flex; gap:8px; overflow:auto; padding-bottom:6px; margin:10px 0}
    .chip{padding:8px 12px; border:1px solid var(--line); border-radius:999px; white-space:nowrap; cursor:pointer}
    .grid{display:grid; grid-template-columns:repeat(2,1fr); gap:10px}
    .card{background:#121212; border:1px solid var(--line); border-radius:14px; overflow:hidden}
    .ph-img{height:110px; background:#0d0d0d; border-bottom:1px solid var(--line); display:flex; align-items:center; justify-content:center; color:var(--muted); font-size:12px}
    .card-body{padding:10px; display:flex; flex-direction:column; gap:6px}
    .title{font-size:13px; line-height:1.2}
    .price{font-weight:700}
    .btn{display:inline-flex; align-items:center; justify-content:center; gap:8px; padding:10px 12px; border-radius:12px; border:1px solid var(--line); background:#161616; color:var(--fg); cursor:pointer}
    .btn.primary{background:var(--accent); color:#0b0b0b; border-color:#1aa651}
    .btn.ghost{background:#131313}
    .row{display:flex; align-items:center; justify-content:space-between}
    .cart-row{display:flex; align-items:center; gap:10px; padding:10px 0; border-bottom:1px dashed var(--line)}
    .cart-thumb{width:52px; height:52px; background:#0d0d0d; border:1px solid var(--line); border-radius:10px; display:flex; align-items:center; justify-content:center; color:var(--muted); font-size:10px}
    .qty{display:inline-flex; align-items:center; justify-content:center; width:26px; height:26px; border:1px solid var(--line); border-radius:8px}
    .total{font-size:18px; font-weight:800}
    .bottom-nav{position:absolute; bottom:0; left:0; right:0; height:56px; border-top:1px solid var(--line); background:#0f0f0f; display:flex}
    .tab{flex:1; display:flex; flex-direction:column; align-items:center; justify-content:center; gap:4px; font-size:11px; color:var(--muted); cursor:pointer}
    .tab.active{color:var(--fg)}
    .spacer{height:10px}
    .note{color:var(--muted); font-size:12px}
    .success{color:#c7ffd9}
    .danger{color:var(--danger)}
    .link{color:var(--accent); text-decoration:none}
  </style>
</head>
<body>
  <div class="phone" role="application" aria-label="Protótipo App Headshop 9:16">
    <div class="statusbar"><span>100%</span><span>●●●</span></div>
    <div class="appbar">
      <div class="logo">Madame Ganja</div>
      <div class="pill" id="cartPill" data-nav="cart">🛒 <span id="cartCount">0</span></div>
    </div>

    <!-- Splash (optional quick) -->
    <section class="screen active" id="splash">
      <div class="content" style="display:flex; height:100%; align-items:center; justify-content:center; text-align:center; gap:16px; flex-direction:column">
        <div style="font-size:22px; font-weight:800">Headshop</div>
        <div class="banner">[ Logo / Arte Splash 9:16 ]</div>
        <button class="btn primary" data-nav="home">Entrar</button>
        <div class="note">Dica: substitua placeholders por seus produtos reais.</div>
      </div>
      <div class="bottom-nav">
        <div class="tab active" data-nav="home">🏠<div>Home</div></div>
        <div class="tab" data-nav="catalogo">🗂️<div>Catálogo</div></div>
        <div class="tab" data-nav="cart">🛒<div>Carrinho</div></div>
      </div>
    </section>

    <!-- Home -->
    <section class="screen" id="home">
      <div class="content">
        <div class="banner">[ Banner/Promo da Semana ]</div>
        <div class="categories">
          <div class="chip" data-category="Piteiras" data-nav="catalogo">Piteiras</div>
          <div class="chip" data-category="Sedas" data-nav="catalogo">Sedas</div>
          <div class="chip" data-category="Isqueiros" data-nav="catalogo">Isqueiros</div>
          <div class="chip" data-category="Cinzeiros" data-nav="catalogo">Cinzeiros</div>
          <div class="chip" data-category="Brindes" data-nav="catalogo">Brindes</div>
        </div>
        <h3 style="margin:8px 0 6px">Destaques</h3>
        <div class="grid">
          <!-- Produto placeholder -->
          <div class="card">
            <div class="ph-img">[Imagem do produto]</div>
            <div class="card-body">
              <div class="title">Nome do Produto</div>
              <div class="price">R$ 0,00</div>
              <button class="btn add">+ Adicionar</button>
            </div>
          </div>
          <div class="card">
            <div class="ph-img">[Imagem do produto]</div>
            <div class="card-body">
              <div class="title">Nome do Produto</div>
              <div class="price">R$ 0,00</div>
              <button class="btn add">+ Adicionar</button>
            </div>
          </div>
        </div>
      </div>
      <div class="bottom-nav">
        <div class="tab active" data-nav="home">🏠<div>Home</div></div>
        <div class="tab" data-nav="catalogo">🗂️<div>Catálogo</div></div>
        <div class="tab" data-nav="cart">🛒<div>Carrinho</div></div>
      </div>
    </section>

    <!-- Catálogo -->
    <section class="screen" id="catalogo">
      <div class="content">
        <div class="row" style="margin: 6px 0 10px">
          <div class="pill" id="currentCat">Categoria: Todas</div>
          <button class="btn ghost" data-nav="home">Voltar</button>
        </div>
        <div class="grid">
          <!-- 6 placeholders prontos -->
          <div class="card"><div class="ph-img">[Imagem]</div><div class="card-body"><div class="title">Produto</div><div class="price">R$ 0,00</div><button class="btn add">+ Adicionar</button></div></div>
          <div class="card"><div class="ph-img">[Imagem]</div><div class="card-body"><div class="title">Produto</div><div class="price">R$ 0,00</div><button class="btn add">+ Adicionar</button></div></div>
          <div class="card"><div class="ph-img">[Imagem]</div><div class="card-body"><div class="title">Produto</div><div class="price">R$ 0,00</div><button class="btn add">+ Adicionar</button></div></div>
          <div class="card"><div class="ph-img">[Imagem]</div><div class="card-body"><div class="title">Produto</div><div class="price">R$ 0,00</div><button class="btn add">+ Adicionar</button></div></div>
          <div class="card"><div class="ph-img">[Imagem]</div><div class="card-body"><div class="title">Produto</div><div class="price">R$ 0,00</div><button class="btn add">+ Adicionar</button></div></div>
          <div class="card"><div class="ph-img">[Imagem]</div><div class="card-body"><div class="title">Produto</div><div class="price">R$ 0,00</div><button class="btn add">+ Adicionar</button></div></div>
        </div>
      </div>
      <div class="bottom-nav">
        <div class="tab" data-nav="home">🏠<div>Home</div></div>
        <div class="tab active" data-nav="catalogo">🗂️<div>Catálogo</div></div>
        <div class="tab" data-nav="cart">🛒<div>Carrinho</div></div>
      </div>
    </section>

    <!-- Carrinho -->
    <section class="screen" id="cart">
      <div class="content">
        <h3 style="margin:6px 0">Seu carrinho</h3>
        <div id="cartList">
          <div class="note">Nada aqui ainda. Adicione produtos no Catálogo.</div>
        </div>
        <div class="spacer"></div>
        <div class="row">
          <div class="total">Total: <span id="total">R$ 0,00</span></div>
          <button class="btn primary" data-nav="checkout">Finalizar compra</button>
        </div>
      </div>
      <div class="bottom-nav">
        <div class="tab" data-nav="home">🏠<div>Home</div></div>
        <div class="tab" data-nav="catalogo">🗂️<div>Catálogo</div></div>
        <div class="tab active" data-nav="cart">🛒<div>Carrinho</div></div>
      </div>
    </section>

    <!-- Checkout -->
    <section class="screen" id="checkout">
      <div class="content">
        <h3>Pagamento</h3>
        <div class="note">Simulação (sem gateway). Escolha uma opção:</div>
        <div style="display:grid; gap:10px; margin:12px 0">
          <button class="btn primary" data-nav="confirm">Pix</button>
          <button class="btn" data-nav="confirm">Cartão</button>
          <button class="btn" data-nav="confirm">Dinheiro na entrega</button>
        </div>
        <button class="btn ghost" data-nav="cart">Voltar ao carrinho</button>
      </div>
      <div class="bottom-nav">
        <div class="tab" data-nav="home">🏠<div>Home</div></div>
        <div class="tab" data-nav="catalogo">🗂️<div>Catálogo</div></div>
        <div class="tab active" data-nav="cart">🛒<div>Carrinho</div></div>
      </div>
    </section>

    <!-- Confirm -->
    <section class="screen" id="confirm">
      <div class="content" style="text-align:center">
        <div style="font-size:28px; font-weight:800; margin-top:30px">Pedido recebido! ✅</div>
        <p class="success">Você receberá os detalhes no WhatsApp.</p>
        <p class="note">Este é um protótipo. Substitua os placeholders por produtos reais e conecte um gateway de pagamento no produto final.</p>
        <button class="btn primary" data-nav="home">Voltar à Home</button>
      </div>
      <div class="bottom-nav">
        <div class="tab active" data-nav="home">🏠<div>Home</div></div>
        <div class="tab" data-nav="catalogo">🗂️<div>Catálogo</div></div>
        <div class="tab" data-nav="cart">🛒<div>Carrinho</div></div>
      </div>
    </section>
  </div>

  <script>
    // Navegação simples entre "telas"
    const screens = Array.from(document.querySelectorAll('.screen'));
    const cartCount = document.getElementById('cartCount');
    const cartList = document.getElementById('cartList');
    const totalEl = document.getElementById('total');
    const currentCat = document.getElementById('currentCat');

    const state = { cart: [], category: 'Todas' };

    function fmt(n){ return n.toLocaleString('pt-BR', { style:'currency', currency:'BRL' }); }

    function show(id){
      screens.forEach(s=>s.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      // tabs visual state
      document.querySelectorAll('.tab').forEach(t=>{
        t.classList.toggle('active', t.dataset.nav===id);
      });
    }

    function renderCart(){
      cartList.innerHTML = '';
      if(state.cart.length===0){
        cartList.innerHTML = '<div class="note">Nada aqui ainda. Adicione produtos no Catálogo.</div>';
      } else {
        state.cart.forEach((item, idx)=>{
          const row = document.createElement('div');
          row.className = 'cart-row';
          row.innerHTML = `
            <div class="cart-thumb">[Img]</div>
            <div style="flex:1">
              <div style="font-weight:600">${item.nome}</div>
              <div class="note">${fmt(item.preco)}</div>
            </div>
            <button class="qty" data-idx="${idx}" data-act="dec">-</button>
            <div class="qty">${item.qtd}</div>
            <button class="qty" data-idx="${idx}" data-act="inc">+</button>
            <button class="btn ghost" data-idx="${idx}" data-act="rm">Remover</button>
          `;
          cartList.appendChild(row);
        });
      }
      const total = state.cart.reduce((s,i)=>s + i.preco * i.qtd, 0);
      totalEl.textContent = fmt(total);
      cartCount.textContent = state.cart.reduce((s,i)=>s+i.qtd,0);
    }

    function addFake(){
      // Produto fictício para o MVP; ao trocar por real, ajuste nome/preço.
      const item = { nome:'Produto', preco:0, qtd:1 };
      const found = state.cart.find(i=>i.nome===item.nome && i.preco===item.preco);
      if(found){ found.qtd++; } else { state.cart.push(item); }
      renderCart();
    }

    document.addEventListener('click', (e)=>{
      const nav = e.target.closest('[data-nav]');
      if(nav){
        if(nav.dataset.category){
          state.category = nav.dataset.category; currentCat.textContent = 'Categoria: ' + state.category;
        }
        show(nav.dataset.nav);
      }
      if(e.target.classList.contains('add')) addFake();
      if(e.target.dataset && e.target.dataset.act){
        const { idx, act } = e.target.dataset;
        const it = state.cart[idx];
        if(!it) return;
        if(act==='inc') it.qtd++;
        if(act==='dec') it.qtd = Math.max(1, it.qtd-1);
        if(act==='rm') state.cart.splice(idx,1);
        renderCart();
      }
    });

    // Atalhos do topo
    document.getElementById('cartPill').addEventListener('click', ()=>show('cart'));

    // Init
    renderCart();
  </script>
</body>
</html>
