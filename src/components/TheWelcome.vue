<template>
  <header class="header">
    Door Sensor
  </header>
  <main class="main">
    <div class="status-aberta" v-if="status == 'Aberta'">
      Aberta
    </div>
    <div class="status-fechada" v-else>
      Fechada
    </div>
  </main>

</template>

<script setup>
import { onMounted, ref } from "vue";
import axios from 'axios';

const status = ref(null);

axios.get('http://localhost:3000/status')
  .then(function (response) {
    status.value = response.data[0];
    console.log(response.data[0]);
  })
  .catch(function (error) {
    console.error(error);
  })

</script>

<style scoped>
.header{
  margin-top: 10%;
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  color: black;
  font-weight: bold;
  font-size: 20px;
  display: flex;
  justify-content: center;
}

.main{
  margin-top: 50%;
  display: flex;
  justify-content: center;
}

.status-aberta{
  background-color: green;
  width: 200px;
  height: 200px;
  border-radius: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-size: 20px;
  font-weight: bold;
}

.status-fechada{
  background-color: red;
  width: 200px;
  height: 200px;
  border-radius: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-size: 20px;
  font-weight: bold;
}
</style>