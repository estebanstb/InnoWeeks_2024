<script setup>

</script>
<template>
    <footer>
  <div class="footer-container">
    <div class="footer-section">
      <h3>Navigation</h3>
      <ul>
        <li><a href="#">Accueil</a></li>
        <li><a href="#">À propos</a></li>
        <li><a href="/search">Rechercher</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </div>
    <div class="footer-section">
      <h3>Contact</h3>
      <p>Email: contact@example.com</p>
      <p>Téléphone: +33 1 23 45 67 89</p>
      <p>Adresse: 123 Rue Exemple, 75000 Paris, France</p>
    </div>
  </div>
  <div class="footer-bottom">
    <p>&copy; 2024 Votre Entreprise. Tous droits réservés.</p>
  </div>
</footer>
</template>
<style scoped>
h3 {
    text-decoration: underline;
}
footer {
    background-color: #0C595E;
    color: #ffffff;
    padding-top: 10px;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
}
.footer-container {
    display: flex;
    justify-content: space-around;
    max-width: 1200px;
    padding-left: 20px;
    padding-right: 20px;
    margin: 0 auto;
}

.footer-section {
    flex: 1;
    padding: 0 20px;
}

.footer-section h3 {
    margin-bottom: 10px;
}

.footer-section ul {
    list-style-type: none;
    padding: 0;
}

.footer-section ul li {
    margin-bottom: 5px;
}

.footer-section ul li a {
    color: #ffffff;
    text-decoration: none;
}

.footer-section ul li a:hover {
    text-decoration: underline;
}

.footer-bottom {
    text-align: center;
    padding: 10px;
    border-top: 1px solid #ffffff;
    margin-top: 10px;
}

.footer-bottom p {
    margin: 0;
}
</style>