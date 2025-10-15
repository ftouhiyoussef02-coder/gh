<!DOCTYPE html>
<html>
<body>
<!-- On met le texte dans le body pour que Thunkable puisse le récupérer -->
<span id="lang"></span>

<script>
  // Récupère la langue du navigateur
  var lang = navigator.language || navigator.userLanguage;

  // Met la langue dans l'élément <span>
  document.getElementById("lang").innerText = lang;
</script>
</body>
</html>
