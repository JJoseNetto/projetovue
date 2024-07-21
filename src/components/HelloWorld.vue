<script setup>
import Header from './headercomponente.vue'
import Footer from './footercomponente.vue'
import { ref } from 'vue';
import jsonData from '../../resources/categorias.json'

const selectedIngredients = ref([]);

const categories = jsonData;

const AdicionaIngrediente = (ingredient) => {
    const index = selectedIngredients.value.indexOf(ingredient);
    if (index === -1) {
    selectedIngredients.value.push(ingredient);
    } else {
    selectedIngredients.value.splice(index, 1);
    }
};

const buscarReceitas = () => {
    if (selectedIngredients.value.length === 0) {
        alert('Por favor, selecione pelo menos um ingrediente.');
        return;
    } else {
    const ingredientes = selectedIngredients.value.join(', ');
    const query = `receitas com esses ingredientes: ${ingredientes}`;
    const url = `https://www.google.com/search?q=${encodeURIComponent(query)}`;
    window.location.href = url;
    }
};
</script>

<template>
    <Header />
    
    <section class="py-5 main-content">
        <div class="container">
            <div id="selected-ingredients" class="mb-4">
                <p class="lista">Sua lista:</p>
                <div id="ingredient-list" class="d-flex flex-wrap ingredientes-escolhidos">
                    <span v-for="(ingredient, index) in selectedIngredients" :key="index" class="badge m-1">{{ ingredient }}</span>
                </div>
            </div>

            <h2 class="text-center">Ingredientes</h2>
            <p class="text-center p-ingredientes">Selecione abaixo os ingredientes que você quer usar nesta receita:</p>
            
            <div class="row">
                <div class="col-md-3 d-flex" v-for="(category, index) in categories" :key="index">
                    <div class="category flex-fill">
                        <img :src="category.icon" alt="">
                        <h4>{{ category.name }}</h4>
                            <button v-for="ingredient in category.ingredients" :key="ingredient" class="btn btn-outline-secondary m-1 ingredient-btn" :class="{ selected: selectedIngredients.includes(ingredient) }" @click="AdicionaIngrediente(ingredient)">{{ ingredient }}</button>
                    </div>
                </div>
            </div>
            <p>*Atenção: consideramos que vc tem em casa sal, pimenta e água.</p>
            <button class="button mx-auto d-block" type="button" @click="buscarReceitas">Buscar Receitas!</button>
        </div>
    </section>

    <Footer />
</template>

<style scoped>
body {
    background-color: #fffaf3;
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
</style>
