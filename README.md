<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Commande de Bijoux Personnalisés</title>

<style>
/* --- GLOBAL --- */
body {
    margin: 0;
    padding: 0;
    font-family: "Georgia", serif;
    background-image: url("https://images.unsplash.com/photo-1519710164239-da123dc03ef4?auto=format&fit=crop&w=2000&q=80");
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    color: #fff;
}

/* --- CONTENEUR --- */
.container {
    max-width: 750px;
    margin: 40px auto;
    padding: 30px;
    background: rgba(0,0,0,0.55);
    border-radius: 12px;
    backdrop-filter: blur(4px);
    box-shadow: 0 0 25px rgba(0,0,0,0.5);
}

/* TITRES */
h1 { text-align:center; font-size:36px; }
h2 { margin-top:25px; border-bottom:1px solid rgba(255,255,255,0.3); padding-bottom:6px; }

/* FORM */
label { display:block; margin:10px 0; font-size:18px; }
input, select, textarea {
    width:100%;
    padding:10px;
    margin-top:5px;
    border-radius:6px;
    border:none;
    font-size:16px;
}

/* TOTAL */
.total {
    font-size:26px;
    font-weight:bold;
    text-align:center;
    background:rgba(255,255,255,0.15);
    padding:15px;
    border-radius:10px;
    margin-top:20px;
}

/* BOUTON */
button {
    width:100%;
    padding:18px;
    font-size:20px;
    font-weight:bold;
    cursor:pointer;
    border:none;
    border-radius:10px;
    background:linear-gradient(135deg,#d4af37,#b8860b);
    color:#000;
    margin-top:25px;
}
button:hover { transform:scale(1.03); }
</style>

<script>
function updateTotal() {
    let total = 0;

    const basePrices = { charm:10, collier:10, collierCharms:20, boucles:20 };
    const base = document.querySelector("input[name='type']:checked");
    if (base) total += basePrices[base.value];

    if (document.getElementById("lait").checked) total += 5;
    if (document.getElementById("crins").checked) total += 5;
    if (document.getElementById("paillettes").checked) total += 5;
    if (document.getElementById("poils").checked) total += 10;
    if (document.getElementById("cheveux").checked) total += 10;
    if (document.getElementById("bracelet").checked) total += 5;
    if (document.getElementById("chaine").checked) total += 10;

    document.getElementById("total").innerText = total + " €";
}
</script>

</head>
<body>
<div class="container">

<h1>Commande de Bijou Personnalisé</h1>

<form action="https://formsubmit.co/TON_EMAIL_ICI" method="POST">

<!-- confirmation auto envoyée au client -->
<input type="hidden" name="_autoresponse" value="Merci pour votre commande ! Voici votre bon de commande :">

<!-- redirection vers une page merci -->
<input type="hidden" name="_next" value="https://google.com">

<h2>Vos coordonnées</h2>

<label>Nom :<input type="text" name="Nom" required></label>
<label>Prénom :<input type="text" name="Prénom" required></label>
<label>Email :<input type="email" name="Email" required></label>
<label>Téléphone :<input type="text" name="Téléphone" required></label>
<label>Adresse postale :<textarea name="Adresse" required></textarea></label>

<h2>Type de bijou</h2>
<label><input type="radio" name="Type" value="Charm (10€)" onclick="updateTotal()"> Charm – 10€</label>
<label><input type="radio" name="Type" value="Collier (10€)" onclick="updateTotal()"> Collier – 10€</label>
<label><input type="radio" name="Type" value="Collier charms (20€)" onclick="updateTotal()"> Collier en charms – 20€</label>
<label><input type="radio" name="Type" value="Boucles (20€)" onclick="updateTotal()"> Boucles d’oreilles – 20€</label>

<h2>Options</h2>

<label><input type="checkbox" name="Lait maternel" id="lait" onclick="updateTotal()"> Lait maternel – 5€</label>
<label><input type="checkbox" name="Crins" id="crins" onclick="updateTotal()"> Crins de cheval – 5€</label>
<label><input type="checkbox" name="Paillettes" id="paillettes" onclick="updateTotal()"> Paillettes – 5€</label>

<label>Couleur des paillettes :
<select name="Couleur paillettes">
    <option>or</option><option>argent</option><option>bleu</option>
    <option>rose</option><option>vert</option><option>rouge</option><option>violet</option>
</select>
</label>

<label><input type="checkbox" name="Poils d'animal" id="poils" onclick="updateTotal()"> Poils d’animal – 10€</label>
<label><input type="checkbox" name="Cheveux" id="cheveux" onclick="updateTotal()"> Cheveux – 10€</label>
<label><input type="checkbox" name="Chaîne bracelet" id="bracelet" onclick="updateTotal()"> Chaîne de bracelet – 5€</label>
<label><input type="checkbox" name="Chaîne collier" id="chaine" onclick="updateTotal()"> Chaîne de collier – 10€</label>

<div class="total">Total : <span id="total">0 €</span></div>

<button type="submit">Envoyer la commande</button>
</form>

</div>
</body>
</html>
