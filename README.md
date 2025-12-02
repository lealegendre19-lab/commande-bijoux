<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Commande de Bijoux Personnalisés</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: url('https://images.unsplash.com/photo-1519710164239-da123dc03ef4?auto=format&fit=crop&w=1400&q=80') no-repeat center center/cover;
            backdrop-filter: blur(3px);
            color: #fff;
        }

        .container {
            background: rgba(0, 0, 0, 0.65);
            margin: 30px auto;
            padding: 25px;
            border-radius: 12px;
            width: 90%;
            max-width: 700px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.5);
        }

        h2 {
            text-align: center;
            color: #f6d89e;
        }

        label {
            font-weight: bold;
            color: #fce5bd;
        }

        input, select {
            width: 100%;
            padding: 10px;
            margin: 8px 0 20px;
            border-radius: 8px;
            border: none;
        }

        button {
            background: #d4af37;
            color: #000;
            padding: 12px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            width: 100%;
        }

        button:hover {
            background: #b8912c;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Commande de Bijoux Personnalisés</h2>

    <form id="orderForm">
        <!-- PARTIE 1 - TYPE DE BIJOU -->
        <h3>Type de bijou</h3>
        <label for="bijou">Choisissez votre bijou :</label>
        <select id="bijou" name="bijou" required>
            <option value="Charm - 10€">Charm - 10€</option>
            <option value="Collier formats divers - 10€">Collier formats divers - 10€</option>
            <option value="Collier en charms - 20€">Collier en charms - 20€</option>
            <option value="Boucles d’oreilles - 20€">Boucles d’oreilles - 20€</option>
        </select>

        <!-- PARTIE 2 - OPTIONS -->
        <h3>Options</h3>

        <label><input type="checkbox" name="options" value="Lait maternel - 5€"> Lait maternel (+5€)</label><br>
        <label><input type="checkbox" name="options" value="Crins de cheval - 5€"> Crins de cheval (+5€)</label><br>
        <label><input type="checkbox" name="options" value="Poils d’animaux - 10€"> Poils d’animaux (+10€)</label><br>
        <label><input type="checkbox" name="options" value="Cheveux - 10€"> Cheveux (+10€)</label><br>
        <label><input type="checkbox" name="options" value="Chaîne de bracelet - 5€"> Chaîne de bracelet (+5€)</label><br>
        <label><input type="checkbox" name="options" value="Chaîne de collier - 10€"> Chaîne de collier (+10€)</label><br>

        <br>

        <label>Paillettes (+5€) :</label>
        <select name="paillettes">
            <option value="Aucune">Aucune</option>
            <option value="Or">Or</option>
            <option value="Argent">Argent</option>
            <option value="Bleu">Bleu</option>
            <option value="Rose">Rose</option>
            <option value="Vert">Vert</option>
            <option value="Rouge">Rouge</option>
            <option value="Violet">Violet</option>
        </select>

        <br><br>

        <!-- PARTIE 3 - COORDONNÉES -->
        <h3>Mes coordonnées</h3>

        <label>Nom :</label>
        <input type="text" name="nom" required>

        <label>Prénom :</label>
        <input type="text" name="prenom" required>

        <label>Adresse :</label>
        <input type="text" name="adresse" required>

        <label>Téléphone :</label>
        <input type="tel" name="telephone" required>

        <label>Adresse mail :</label>
        <input type="email" name="email" required>

        <button type="submit">Envoyer ma commande</button>
    </form>
</div>

<script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
<script>
    emailjs.init("lea.legendre19@gmail.com"); 

    document.getElementById("orderForm").addEventListener("submit", function(event) {
        event.preventDefault();

        emailjs.sendForm("service_xxx", "template_xxx", this)
        .then(() => {
            alert("Votre commande a bien été envoyée !");
        }, (error) => {
            alert("Erreur : " + JSON.stringify(error));
        });
    });
</script>

</body>
</html>
