<template>
  <div class="container" v-if="data">
    <h1>{{ data.titulo }}</h1>
    <p>{{ data.descricao }}</p>

    <div class="cards">
      <div class="card" v-for="(img, i) in data.imagens" :key="i">
        <img :src="img" alt="Imagem" />
      </div>
    </div>
  </div>
</template>

<script setup>
const { data, pending, error } = await useFetch("http://127.0.0.1:8000/api/info/")

if (error.value) {
  console.error("Erro ao buscar API:", error.value)
}
</script>

<style scoped>
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
