<script setup>
import { ref } from 'vue';

const selectedIngredients = ref([]);

const categories = [
    {
      name: 'Laticínios e Ovos',
      icon: 'https://cdn-icons-png.flaticon.com/128/2137/2137681.png',
      ingredients: ['Ovos', 'Leite', 'Manteiga', 'Creme de leite', 'Iogurte', 'Leite Condensado'],
    },
    {
      name: 'Farinhas e Fermentos',
      icon: 'https://cdn-icons-png.flaticon.com/128/2098/2098457.png',
      ingredients: ['Canjica', 'Fermento', 'Polvilho', 'Linhaça', 'Farinha de trigo', 'Farinha de mandioca', 'Fubá'],
    },
    {
      name: 'Temperos e Especiarias',
      icon: 'https://cdn-icons-png.flaticon.com/128/5862/5862835.png',
      ingredients: ['Canela', 'Cravo', 'Orégano', 'Noz moscada', 'Tomilho', 'Pimenta do Reino', 'Cominho'],
    },
    {
      name: 'Óleos, Gorduras e Acetos',
      icon: 'https://cdn-icons-png.flaticon.com/128/99/99952.png',
      ingredients: ['Vinagre', 'Óleo', 'Dendê', 'Azeite de Oliva', 'Banha', 'Aceto Balsâmico'],
    },
    {
      name: 'Hortaliças e Verduras',
      icon: 'https://cdn-icons-png.flaticon.com/128/2329/2329903.png',
      ingredients: ['Cebola', 'Alho', 'Tomate', 'Abóbora', 'Abobrinha', 'Batata', 'Pimentão', 'Cenoura'],
    },
    {
      name: 'Açúcares e Adoçantes',
      icon: 'https://cdn-icons-png.flaticon.com/128/5836/5836986.png',
      ingredients: ['Açúcar Branco', 'Stevia', 'Mel', 'Melado', 'Açúcar Mascavo', 'Baunilha', 'Xilitol', 'Glicose'],
    },
    {
      name: 'Proteínas Animais',
      icon: 'https://cdn-icons-png.flaticon.com/128/9340/9340812.png',
      ingredients: ['Carne Bovina', 'Carne Suína', 'Frango', 'Bacon', 'Presunto', 'Calabresa', 'Peixe', 'Miúdos'],
    },
    {
      name: 'Grãos e Cereais',
      icon: 'https://cdn-icons-png.flaticon.com/128/2829/2829956.png',
      ingredients: ['Arroz', 'Feijão', 'Lentilha', 'Grão-de-Bico', 'Quinoa', 'Milho', 'Ervilha'],
    },
    {
      name: 'Frutas Frescas',
      icon: 'https://cdn-icons-png.flaticon.com/128/10981/10981617.png',
      ingredients: ['Banana', 'Maçã', 'Uva', 'Pêra', 'Morango', 'Laranja', 'Abacaxi', 'Coco'],
    },
    {
      name: 'Frutas Secas',
      icon: 'https://cdn-icons-png.flaticon.com/128/8080/8080628.png',
      ingredients: ['Castanhas', 'Damasco', 'Castanha do Pará', 'Pistache', 'Nozes', 'Pinoli', 'Amendoim'],
    },
    {
      name: 'Pães e Massas',
      icon: 'https://cdn-icons-png.flaticon.com/128/2862/2862159.png',
      ingredients: ['Pão', 'Pão Sírio', 'Tortilha', 'Macarrão', 'Nhoque', 'Lasanha', 'Broa', 'Pastel'],
    },
    {
      name: 'Doces e Guloseimas',
      icon: 'https://cdn-icons-png.flaticon.com/128/2066/2066208.png',
      ingredients: ['Doce de Leite', 'Chocolate', 'Chantilly', 'Geleia', 'Goiabada', 'Caramelo', 'Gelatina'],
    },
];

const AdicionaIngrediente = (ingredient) => {
  const index = selectedIngredients.value.indexOf(ingredient);
  if (index === -1) {
    selectedIngredients.value.push(ingredient);
  } else {
    selectedIngredients.value.splice(index, 1);
  }
};


</script>

<template>
<header class="banner d-flex align-items-center">
        <div class="container text-white text-center">
            <img src="/public/images/logo.svg" alt="Cookin'UP Logo" class="mb-4 logo-left">
            <h1><span class="text-green">Um banquete de <br> ideias para</span><br> despertar o chef que <br> há em você!</h1>
            <p>Explore novas receitas todos os dias com <br> os ingredientes que estão ao seu alcance!</p>
            <img src="/public/images/foto-banner.png" alt="Chef" class="chef-image">
        </div>
    </header>
    
    <section class="py-5 main-content">
        <div class="container">
            <div id="selected-ingredients" class="mb-4">
                <p class="lista">Sua lista:</p>
                <div id="ingredient-list" class="d-flex flex-wrap ingredientes-escolhidos">
                  <span v-for="(ingredient, index) in selectedIngredients" :key="index" class="badge m-1">
                    {{ ingredient }}
                  </span>
                </div>
            </div>

            <h2 class="text-center">Ingredientes</h2>
            <p class="text-center p-ingredientes">Selecione abaixo os ingredientes que você quer usar nesta receita:</p>
            
            <div class="row">
                <div class="col-md-3 d-flex" v-for="(category, index) in categories" :key="index">
                    <div class="category flex-fill">
                      <img :src="category.icon" alt="">
                      <h4>{{ category.name }}</h4>
                          <button v-for="ingredient in category.ingredients" :key="ingredient" class="btn btn-outline-secondary m-1 ingredient-btn" :class="{ selected: selectedIngredients.includes(ingredient) }" @click="AdicionaIngrediente(ingredient)">
                            {{ ingredient }}
                          </button>
                    </div>
                </div>
            </div>
            <p>*Atenção: consideramos que vc tem em casa sal, pimenta e água.</p>
            <button class="button mx-auto d-block" type="button"> Buscar Receitas!</button>
        </div>
    </section>

    <footer class="footer mt-auto py-3">
        <div class="container">
            <span class="span-footer"> &reg; Desenvolvido por José Neto |  2024 - Projeto fictício sem fins comerciais.</span>
        </div>
    </footer>

</template>

<style scoped>
body {
    background-color: #fffaf3;
}

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

.main-content {
    border-radius: 50px;
    margin-top: -50px;
    background-color: #fffaf3;
}

.lista{
    text-align: center;
    font-size: 25px;
    color: orange;
}

.ingredientes-escolhidos{
    font-size: 20px;
    padding-bottom: 50px;
    justify-content: center; 
}

.ingredient-btn.selected {
    background-color: #f0633c;  
    color: #ffffff;
    border-color: transparent;
}

span {
    color: rgb(255, 255, 255);
    background-color: #f0633c;
    border-radius: 40px;
}

h2{
    font-size: 40px;
    color: green;
}

.p-ingredientes{
    padding-top: 10px;
    color: green;
}

.category{
    text-align: center;
    background-color: white;
    border-radius: 20px;
    padding: 20px 0px;
    margin-bottom: 20px;
    box-shadow: 5px 5px 10px rgba(94, 94, 94, 0.5);
}

.category img{
    max-height: 50px;
}

h4{
    color: green;
    padding-bottom: 15px;
}

.button{
    color: white;
    background-color: #f0633c;
    border-radius: 80px;
    border-color: transparent;
    padding: 7px 50px;
    margin-top: 80px;
}

.footer {
    background-color: #2F4F4F;
    color: #ffffff;
    text-align: center;
    padding: 10px 0;
    margin-top: auto;
}

.span-footer {
    background-color: transparent;
}
</style>
