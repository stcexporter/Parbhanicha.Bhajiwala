<!DOCTYPE html>
<html lang="mr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>परभणीचा भाजीवाला</title>

<style>
*{box-sizing:border-box}
body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#f5fff3;
  color:#222;
}
header{
  background:#198754;
  color:white;
  text-align:center;
  padding:22px 12px;
}
header h1{margin:0;font-size:30px}
header p{margin:7px 0 0}

.container{
  max-width:900px;
  margin:auto;
  padding:15px;
}

.info{
  background:white;
  border-radius:15px;
  padding:15px;
  margin-bottom:15px;
  box-shadow:0 2px 8px #ccc;
  text-align:center;
}

.products{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(145px,1fr));
  gap:12px;
}

.product{
  background:white;
  border-radius:15px;
  padding:15px;
  text-align:center;
  box-shadow:0 2px 7px #ddd;
}

.product .emoji{font-size:42px}
.product h3{margin:8px 0}
.price{
  font-weight:bold;
  color:#198754;
  margin-bottom:10px;
}

button{
  border:0;
  border-radius:10px;
  padding:10px 14px;
  cursor:pointer;
  font-weight:bold;
}

.add{
  background:#198754;
  color:white;
}

.cart{
  background:white;
  margin-top:20px;
  padding:18px;
  border-radius:15px;
  box-shadow:0 2px 8px #ccc;
}

.cart-item{
  display:flex;
  justify-content:space-between;
  padding:8px 0;
  border-bottom:1px solid #ddd;
}

.whatsapp{
  width:100%;
  background:#25D366;
  color:white;
  font-size:18px;
  margin-top:15px;
}

footer{
  text-align:center;
  padding:25px;
  color:#555;
}
</style>
</head>

<body>

<header>
  <h1>🥬 परभणीचा भाजीवाला 🍅</h1>
  <p>ताजी भाजीपाला व फळे थेट आपल्या घरापर्यंत</p>
</header>

<div class="container">

<div class="info">
  <b>📲 ऑर्डर वेळ:</b> सकाळी 7 ते 11<br>
  <b>🚚 डिलिव्हरी:</b> सकाळी 11 ते दुपारी 4<br>
  <b>🛵 घरपोच डिलिव्हरी उपलब्ध</b>
</div>

<h2>🥦 भाजीपाला</h2>

<div class="products">

<div class="product">
<div class="emoji">🥔</div>
<h3>बटाटा</h3>
<div class="price">₹25 / किलो</div>
<button class="add" onclick="add('बटाटा',25)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🧅</div>
<h3>कांदा</h3>
<div class="price">₹50 / किलो</div>
<button class="add" onclick="add('कांदा',50)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🍅</div>
<h3>टोमॅटो</h3>
<div class="price">₹30 / किलो</div>
<button class="add" onclick="add('टोमॅटो',30)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🥕</div>
<h3>गाजर</h3>
<div class="price">₹20 / 250 ग्रॅम</div>
<button class="add" onclick="add('गाजर',20)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🫑</div>
<h3>ढोबळी मिरची</h3>
<div class="price">₹20 / 250 ग्रॅम</div>
<button class="add" onclick="add('ढोबळी मिरची',20)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🌶️</div>
<h3>मिरची</h3>
<div class="price">₹20 / 250 ग्रॅम</div>
<button class="add" onclick="add('मिरची',20)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🥒</div>
<h3>काकडी</h3>
<div class="price">₹20 / 250 ग्रॅम</div>
<button class="add" onclick="add('काकडी',20)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🍆</div>
<h3>वांगी</h3>
<div class="price">₹20 / 250 ग्रॅम</div>
<button class="add" onclick="add('वांगी',20)">कार्टमध्ये टाका</button>
</div>

<div class="product">
<div class="emoji">🍌</div>
<h3>केळी</h3>
<div class="price">₹40 / डझन</div>
<button class="add" onclick="add('केळी',40)">कार्टमध्ये टाका</button>
</div>

</div>

<div class="cart">
<h2>🛒 तुमची ऑर्डर</h2>

<div id="cartItems">
<p>अजून कोणतीही भाजी निवडलेली नाही.</p>
</div>

<h3>एकूण: ₹<span id="total">0</span></h3>

<button class="whatsapp" onclick="sendWhatsApp()">
📲 WhatsApp वर ऑर्डर पाठवा
</button>
</div>

</div>

<footer>
परभणीचा भाजीवाला<br>
📞 8805930545<br>
ताजी भाजी • योग्य दर • घरपोच सेवा
</footer>

<script>

let cart = [];

function add(name,price){

  let item = cart.find(x => x.name === name);

  if(item){
    item.qty++;
  }else{
    cart.push({
      name:name,
      price:price,
      qty:1
    });
  }

  showCart();
}

function showCart(){

  let box = document.getElementById("cartItems");
  let total = 0;

  if(cart.length === 0){
    box.innerHTML="<p>अजून कोणतीही भाजी निवडलेली नाही.</p>";
    document.getElementById("total").innerText="0";
    return;
  }

  box.innerHTML="";

  cart.forEach((item,index)=>{

    let amount=item.price*item.qty;
    total+=amount;

    box.innerHTML += `
      <div class="cart-item">
        <span>
          ${item.name} × ${item.qty}
        </span>

        <span>
          ₹${amount}
          <button onclick="removeItem(${index})">❌</button>
        </span>
      </div>
    `;
  });

  document.getElementById("total").innerText=total;
}

function removeItem(index){
  cart.splice(index,1);
  showCart();
}

function sendWhatsApp(){

  if(cart.length===0){
    alert("कृपया आधी भाजी निवडा.");
    return;
  }

  let message="🥬 *परभणीचा भाजीवाला - ऑर्डर*%0A%0A";

  cart.forEach(item=>{
    message +=
      "• "+item.name+
      " × "+item.qty+
      " = ₹"+(item.price*item.qty)+
      "%0A";
  });

  let total=cart.reduce(
    (sum,item)=>sum+(item.price*item.qty),0
  );

  message +=
    "%0A💰 *एकूण: ₹"+total+"*"+
    "%0A%0A📍 कृपया माझा पत्ता/लोकेशन पाठवा.";

  let phone="918805930545";

  window.open(
    "https://wa.me/"+phone+"?text="+message,
    "_blank"
  );
}

</script>

</body>
</html>
