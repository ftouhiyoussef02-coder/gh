<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lang Detector for Thunkable</title>
  <!-- Script nécessaire pour la communication avec Thunkable -->
  <script src="https://thunkable.github.io/webviewer-extension/thunkableWebviewerExtension.js" type="text/javascript"></script>
</head>
<body>
  <h2>Détection automatique de la langue 🌐</h2>
  <p id="info">Détection en cours...</p>

  <script>
    // Fonction d'envoi à Thunkable
    function sendToThunkable(message) {
      if (window.ThunkableWebviewerExtension && window.ThunkableWebviewerExtension.postMessage) {
        ThunkableWebviewerExtension.postMessage(message);
      } else {
        console.log("ThunkableWebviewerExtension non détectée. Message:", message);
      }
    }

    // Étape 1 : détecter la langue du navigateur
    const userLang = (navigator.language || navigator.userLanguage || "").toLowerCase(); // ex: "fr-FR"

    // Étape 2 : déterminer la langue parmi les principales
    let detectedLang = "";

    if (userLang.startsWith("ar")) {
      detectedLang = "arabe";
    } else if (userLang.startsWith("zh")) {
      detectedLang = "chinois";
    } else if (userLang.startsWith("fr")) {
      detectedLang = "français";
    } else if (userLang.startsWith("en")) {
      detectedLang = "anglais";
    } else {
      detectedLang = "autre (" + userLang + ")";
    }

    // Étape 3 : afficher la langue détectée
    document.getElementById("info").innerHTML = "Langue détectée : <b>" + detectedLang + "</b>";

    // Étape 4 : envoyer la langue à Thunkable
    sendToThunkable(detectedLang);
  </script>
</body>
</html>

</html>

