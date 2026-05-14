<script setup>
// Props
const props = defineProps({
  question: String,
  optionA: String,
  optionB: String,
})

// Emit choice
const emit = defineEmits(['choice-made'])

function selectChoice(choice) {
  emit('choice-made', choice)
}
</script>

<template>
  <div class="question-card">
    <p class="question-text">{{ props.question }}</p>

    <div class="options">
      <label>
        <input
          type="radio"
          name="choice"
          :value="props.optionA"
          @change="selectChoice(props.optionA)"
        />
        {{ props.optionA }}
      </label>

      <label>
        <input
          type="radio"
          name="choice"
          :value="props.optionB"
          @change="selectChoice(props.optionB)"
        />
        {{ props.optionB }}
      </label>
    </div>
  </div>
</template>

<style scoped>
.question-card {
  border: 2px dashed #3b82f6;
  border-radius: 8px;
  padding: 1.5rem;
  margin-top: 1rem;
}

.question-text {
  font-weight: bold;
  font-size: 1.1rem;
  margin-bottom: 1rem;
  text-align: center;
}

.options {
  display: flex;
  gap: 2rem;
  justify-content: center;
}

label {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  cursor: pointer;
}
</style>