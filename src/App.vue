<script setup lang="ts">
import { ref } from 'vue';

const noButton = ref<HTMLButtonElement | null>(null);
const step = ref(1)

const moveButton = () => {
  const button = noButton.value;
  if (button) {
    const container = button.parentElement;
    if (container) {
      const containerRect = container.getBoundingClientRect();
      const maxX = containerRect.width - button.offsetWidth;
      const maxY = containerRect.height - button.offsetHeight;

      let randomX, randomY;
      do {
        randomX = Math.random() * maxX;
        randomY = Math.random() * maxY;
      } while (
        Math.abs(randomX - parseFloat(button.style.left || '0')) < 50 ||
        Math.abs(randomY - parseFloat(button.style.top || '0')) < 50
      );

      button.style.position = 'absolute';
      button.style.left = `${randomX}px`;
      button.style.top = `${randomY}px`;
    }
  }
};

const accept = () => {
  step.value = 2;

};
</script>
<template>
  <div v-if="step === 1" class="container">
    <h1>Oii Sofia, eu queria saber se você quer namorar comigo?! 🥰</h1>
    <h3> eu queria deixar claro mais uma vez que eu sou pessimo com palavras, eu queria te dizer que eu te amo demais, vc chegou na minha vida em um momento que eu menos esperava achar alguém, vc mudou minha vida fazendo ela ficar divertida todo dia, mesmo longe eu fico rindo dos seus stories no pvd, lembrando da gnt junto e rindo de fofocas que vc me conta, eu amo a forma que você me trata, a maneira que você me olhar e o jeito que vc sorri pra mim, vc me faz o homem mais feliz do mundo, eu sinto que com você do meu lado eu sempre serei mais feliz, eu te amo demais e obrigado por tudo minha princesa, eu prometo que vou te fazer a pessoa mais feliz do mundo, eu sou muito apaixonado em você e com isso eu quero saber, quer namorar comigo?</h3>
    <div class="buttons">
      <button class="accept-button" @click="accept">Sim</button>
      <button
        ref="noButton"
        @mouseenter="moveButton"
        class="no-button"
      >
        Não
      </button>
    </div>
  </div>
  <div v-if="step === 2" class="container">
    <h2>Que bom amor, hahahah!</h2>
    <h3>Eu te Amo Demais vida 🥰</h3>

  </div>
</template>



<style>
.container {
  text-align: center;
  margin-top: 10%;
  font-family: Arial, sans-serif;
}

h1 {
  font-size: 2rem;
  margin-bottom: 2rem;
}

.buttons {
  position: relative;
  width: 300px;
  height: 200px;
  margin: 0 auto;

}

.accept-button {
  color: #ffffff;
}

button {
  padding: 10px 20px;
  font-size: 1rem;
  cursor: pointer;
  border: 2px solid #333;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #f0f0f0;
}

.no-button {
  background-color: #ffcccc;
  position: absolute;
}
</style>
