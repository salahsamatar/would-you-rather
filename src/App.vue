<script setup>
import { ref } from 'vue'
import WouldYouRather from './components/WouldYouRather.vue'

// Parent data
const question = ref('Would you rather have the ability to fly or be invisible?')
const optionA = ref('Fly')
const optionB = ref('Be invisible')
const userChoice = ref(null)

// Choice handler
function handleChoice(choice) {
  userChoice.value = choice
}
</script>

<template>
  <div class="app-container">
    <h1>Would you rather...</h1>
    <WouldYouRather
      :question="question"
      :option-a="optionA"
      :option-b="optionB"
      @choice-made="handleChoice"
    />

    <p v-if="userChoice" class="result-message">
      You chose: <strong>{{ userChoice }}</strong>
    </p>
    <p v-else class="prompt-message">Pick one of the options above.</p>
  </div>
</template>

<style scoped>
.app-container {
  max-width: 600px;
  margin: 2rem auto;
  padding: 2rem;
  border: 2px dashed #22c55e;
  border-radius: 8px;
  font-family: sans-serif;
  text-align: center;
}

h1 {
  font-size: 1.8rem;
  margin-bottom: 0.5rem;
}

.result-message {
  margin-top: 1.2rem;
  font-size: 1rem;
  color: #374151;
}

.prompt-message {
  margin-top: 1.2rem;
  color: #6b7280;
  font-style: italic;
}
</style>