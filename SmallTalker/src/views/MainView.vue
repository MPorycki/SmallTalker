<template>
  <div class="container">
    <!-- Big Label at the Top -->
    <h1 class="page-title">Small Talker</h1>

    <!-- Text Output Box -->
    <div class="output-box">
      <p>{{ textOutput }}</p>
    </div>

    <!-- Button -->
    <button @click="handleClick">Click Me</button>

    <!-- Label for Checkbox Group -->
    <div class="checkbox-group">
      <label class="checkbox-group-label">Available categories:</label>

      <!-- Checkboxes for Multi-Select -->
      <label v-for="option in categories" :key="option.value" class="checkbox-label">
        <input type="checkbox" :value="option.value" v-model="selectedCategories" />
        {{ option.text }}
      </label>
    </div>
  </div>
</template>

<script>
import questions from '../assets/questions.json'
export default {
  data() {
    return {
      questionsDb: questions,
      textOutput: 'Your question to ask will appear here!',
      selectedCategories: [
        'currentEvents',
        'entertainment',
        'foodAndDrinks',
        'weather',
        'weekendPlans'
      ],
      categories: [
        { value: 'currentEvents', text: 'Current Events (Light or Local)' },
        { value: 'entertainment', text: 'Entertainment' },
        { value: 'foodAndDrinks', text: 'Food And Drinks' },
        { value: 'weather', text: 'Weather' },
        { value: 'weekendPlans', text: 'Weekend Plans' }
      ]
    }
  },
  methods: {
    handleClick() {
      // Handle button click event
      this.textOutput = `${this.drawQuestion()}`
    },
    getRandomNumber(max) {
      return Math.floor(Math.random() * max)
    },
    drawQuestion() {
      // Select a random category
      var selectedCategoriesLength = this.selectedCategories.length
      var category = this.selectedCategories[this.getRandomNumber(selectedCategoriesLength)]

      // Pick a question from the selected category
      var questionsArrayLength = this.questionsDb[category].length
      var question = this.questionsDb[category][this.getRandomNumber(questionsArrayLength)]
      return question
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-self: center;
  width: 15vw;
  max-width: 600px; /* Adjust this value as needed */
}

.page-title {
  font-size: 2em;
  margin-bottom: 20px;
  text-align: center;
}

.output-box {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  width: 100%; /* Ensure it takes full width of the container */
  text-align: center;
  background-color: #f9f9f9;
  box-sizing: border-box; /* Include padding in width calculations */
}

button {
  margin-bottom: 10px;
  padding: 10px 20px;
  cursor: pointer;
  width: 100%;
  max-width: 300px;
}

.checkbox-group {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.checkbox-group-label {
  font-weight: bold;
  margin-bottom: 5px;
}

.checkbox-label {
  margin-bottom: 5px;
  display: flex;
  align-items: center;
}

input[type='checkbox'] {
  margin-right: 10px;
}
</style>
