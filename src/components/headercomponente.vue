<template>
    <header class="banner d-flex align-items-center">
        <div class="container text-white text-center">
            <img src="/public/images/logo.svg" alt="Cookin'UP Logo" class="mb-4 logo-left">
            <h1><span class="text-green">Um banquete de <br> ideias para</span><br> despertar o chef que <br> há em você!</h1>
            <p>Explore novas receitas todos os dias com <br> os ingredientes que estão ao seu alcance!</p>
            <img src="/public/images/foto-banner.png" alt="Chef" class="chef-image">
        </div>
    </header>
</template>

<style>
.banner {
    background-color: #263b29;
    background-image: url('../images/fundo-banner.png');
    background-size: cover;
    background-position: center;
    color: white;
    height: 70vh;
    position: relative;
    z-index: -1;
}

.banner .container {
    position: relative;
    z-index: 2;
}

.logo-left {
    display: block;
    margin-left: 0;
    width: 12%;
    margin-right: 20px;
}

.banner .chef-image {
    position: absolute;
    bottom: 0;
    right: 0;
    max-height: 120%;
    width: auto;
}

header h1 {
    text-align: start;
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 1rem;
}

.text-green {
    color: green;
    background-color: transparent;
}

header {
    padding-bottom: 50px;
}

header p {
    text-align: start;
    font-size: 1.25rem;
}

@media (max-width: 659px) {

.logo-left {
  display: block;
  margin-left: 0;
  width: 80px;
  margin-right: 20px;
}

.banner .chef-image {
  position: absolute;
  bottom: 0;
  right: 0;
  max-height: 90%;
  width: auto;
}

header h1 {
  text-align: start;
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 1rem;
}

header p {
  text-align: start;
  font-size: 10px;
}

}
</style>
