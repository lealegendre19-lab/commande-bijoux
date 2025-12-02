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

/* --- CONTENEUR PRINCIPAL --- */
.container {
    max-width: 750px;
    margin: 40px auto;
    padding: 30px;
    background: rgba(0, 0, 0, 0.55);
    border-radius: 12px;
    backdrop-filter: blur(4px);
    box-shadow: 0 0 25px rgba(0,0,0,0.5);
}

/* --- TITRE --- */
h1 {
    text-align: center;
    font-size: 36px;
    margin-bottom: 10px;
    letter-spacing: 1px;
}

/* --- SOUS-TITRE --- */
h2 {
    margin-top: 25px;
    font-size: 26px;
    border-bottom: 1px solid rgba(255,255,255,0.3);
    padding-bottom: 6px;
}

/* --- SECTIONS --- */
section {
    margin-bottom: 25px;
}

/* --- LABELS --- */
label {
    display: block;
    margin: 10px 0;
    cursor: pointer;
    font-size: 18px;
}

/* --- SELECT --- */
select {
    padding: 8px;
    border-radius: 6px;
    border: none;
    background: rgba(255,255,255,0.9);
    font-size: 16px;
}

/* --- TOTAL --- */
.total {
    font-size: 28px;
    font-weight: bold;
    text-align: center;
    margin-top: 20px;
    background: rgba(255,255,255,0.15);
    padding: 15px;
    border-radius: 10px;
}

/* --- BOUTON --- */
button {
    width: 100%;
    padding: 18px;
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
    border: none;
    border-radius: 10px;
    background: linear-gradient(135deg, #d4af37, #b8860b);
    color: #000;
    margin-top: 20px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.4);
    transition: 0.2s;
}
button:hover {
    transform: scale(1.03);
    box-shadow: 0 6px 18px rgba(0,0,0,0.5);
}
</style>

<script>
function updateTotal() {
    let total = 0;

    const basePrices = {
        "charm": 10,
        "collier": 10,
        "collierCharms": 20,
        "boucles": 20
    };

    const baseChoice = document.querySelector("input[name='type']:checked");
    if (baseChoice) total += basePrices[baseChoice.value];

    if (document.getElementById("lait").checked) total += 5;
    if (document.getElementById("crins").checked) total += 5;
    if (document.getElementById("paillettes").checked) total += 5;
    if (document.getElementById("poils").checked) total += 10;
    if (document.getElementById("cheveux").checked) total += 10;
    if (document.getElementById("bracelet").checked) total += 5;
    if (document.getElementById("chaine").checked) total += 10;

    document.getElementById("total").innerText = total + " €";
}

function envoyerCommande() {
    let contenu = "Nouvelle commande :%0D%0A";

    const type = document.querySelector("input[name='type']:checked");
    if (type) contenu += "- Bijou : " + type.nextElementSibling.innerText + "%0D%0A";

    const options = [
        ["lait", "Lait maternel"],
        ["crins", "Crins de cheval"],
        ["paillettes", "Paillettes (" + document.getElementById("couleurPaillettes").value + ")"],
        ["poils", "Poils d'animal"],
        ["cheveux", "Cheveux"],
        ["bracelet", "Chaîne bracelet"],
        ["chaine", "Chaîne collier"]
    ];

    contenu += "%0D%0AOptions :%0D%0A";
    options.forEach(o => {
        if (document.getElementById(o[0]).checked) {
            contenu += "- " + o[1] + "%0D%0A";
        }
    });

    contenu += "%0D%0ATotal : " + document.getElementById("total").innerText;

    window.location.href = "mailto:TON_EMAIL_ICI?subject=Commande Bijou&body=" + contenu;
}
</script>
</head>

<body>
<div class="container">

<h1>Commande de Bijoux</h1>

<section>
<h2>Type de bijou</h2>
<label><input type="radio" name="type" value="charm" onclick="updateTotal()"> Charm – 10€</label>
<label><input type="radio" name="type" value="collier" onclick="updateTotal()"> Collier (formats divers) – 10€</label>
<label><input type="radio" name="type" value="collierCharms" onclick="updateTotal()"> Collier en charms – 20€</label>
<label><input type="radio" name="type" value="boucles" onclick="updateTotal()"> Boucles d’oreilles – 20€</label>
</section>

<section>
<h2>Options</h2>

<label><input type="checkbox" id="lait" onclick="updateTotal()"> Lait maternel – 5€</label>
<label><input type="checkbox" id="crins" onclick="updateTotal()"> Crins de cheval – 5€</label>

<label><input type="checkbox" id="paillettes" onclick="updateTotal()"> Paillettes – 5€</label>
<label>Couleur :
<select id="couleurPaillettes">
    <option>or</option>
    <option>argent</option>
    <option>bleu</option>
    <option>rose</option>
    <option>vert</option>
    <option>rouge</option>
    <option>violet</option>
</select>
</label>

<label><input type="checkbox" id="poils" onclick="updateTotal()"> Poils d’animal – 10€</label>
<label><input type="checkbox" id="cheveux" onclick="updateTotal()"> Cheveux – 10€</label>
<label><input type="checkbox" id="bracelet" onclick="updateTotal()"> Chaîne de bracelet – 5€</label>
<label><input type="checkbox" id="chaine" onclick="updateTotal()"> Chaîne de collier – 10€</label>
</section>

<div class="total">Total : <span id="total">0 €</span></div>

<button onclick="envoyerCommande()">Envoyer la commande par email</button>

</div>
</body>
</html>
