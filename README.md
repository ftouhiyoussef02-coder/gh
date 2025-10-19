<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lang Detector for Thunkable</title>
  <!-- 🔗 Lien vers la bibliothèque Thunkable (OBLIGATOIRE pour communiquer) -->
  <script src="https://thunkable.github.io/webviewer-extension/thunkableWebviewerExtension.js" type="text/javascript"></script>
</head>
<body>
  <h2>Détection automatique de la langue 🌐</h2>
  <p id="info">Détection en cours...</p>

  <script>
    // Fonction pour envoyer un message à Thunkable
    function sendToThunkable(message) {
      if (window.ThunkableWebviewerExtension && window.ThunkableWebviewerExtension.postMessage) {
        ThunkableWebviewerExtension.postMessage(message);
      } else {
        console.log("ThunkableWebviewerExtension non détectée. Message:", message);
      }
    }

    // Étape 1 : détecter la langue du device/navigateur
    const userLang = navigator.language || navigator.userLanguage; // ex: "fr-FR", "ar-TN", "en-US"

    // Étape 2 : afficher l’info à l’écran
    document.getElementById("info").innerHTML = "Langue détectée : <b>" + userLang + "</b>";

    // Étape 3 : envoyer cette info à Thunkable
    sendToThunkable("Langue détectée : " + userLang);

    // (Optionnel) Envoie aussi un message de test
    sendToThunkable("hello world");
  </script>
</body>
</html>

