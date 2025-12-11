<template>
  <div class="container" v-if="data">
    <h1>{{ data.titulo }}</h1>
    <p>{{ data.descricao }}</p>

    <div class="cards">
      <div class="card" v-for="(img, i) in data.imagens" :key="i">
        <img :src="img" alt="Imagem carregada" />
      </div>
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      data: {
        titulo: "Carregando...",
        descricao: "Aguarde...",
        imagens: []
      }
    };
  },
  async mounted() {
    try {
      const response = await axios.get("http://127.0.0.1:8000/api/info/");
      this.data = response.data;
    } catch (error) {
      console.error(error);
    }
  }
};
</script>

<style>
body {
  background: #ffffff;
  color: #000;
  font-family: Arial, sans-serif;
}

.container {
  max-width: 900px;
  margin: 40px auto;
  padding: 20px;
  text-align: center;
}

.cards {
  margin-top: 30px;
  display: flex;
  gap: 20px;
  justify-content: center;
  flex-wrap: wrap;
}

.card {
  background: #f5f5f5;
  padding: 10px;
  border-radius: 12px;
  width: 250px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.card img {
  width: 100%;
  border-radius: 10px;
}
</style>
