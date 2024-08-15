<template>
    <div class="container">
      <!-- Big Label at the Top -->
      <h1 class="page-title">Small Talker</h1>
  
      <!-- Text Output Box -->
      <div class="output-box">
        <p>{{ textOutput }}</p>
      </div>
      
      <!-- Button -->
      <button @click="handleClick">
        Click Me
      </button>
  
      <!-- Label for Checkbox Group -->
      <div class="checkbox-group">
        <label class="checkbox-group-label">Available categories:</label>
  
        <!-- Checkboxes for Multi-Select -->
        <label v-for="option in options" :key="option.value" class="checkbox-label">
          <input type="checkbox" :value="option.value" v-model="selectedOptions" />
          {{ option.text }}
        </label>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        textOutput: 'Your text will appear here...',
        selectedOptions: [],
        options: [
          { value: 'option1', text: 'Option 1' },
          { value: 'option2', text: 'Option 2' },
          { value: 'option3', text: 'Option 3' },
        ]
      };
    },
    methods: {
      handleClick() {
        // Handle button click event
        this.textOutput = `Selected options: ${this.selectedOptions.join(', ')}`;
      }
    }
  }
  </script>
  
  <style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
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
    width: 100%;
    text-align: center;
    background-color: #f9f9f9;
  }
  
  button {
    margin-bottom: 10px;
    padding: 10px 20px;
    cursor: pointer;
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
  
  input[type="checkbox"] {
    margin-right: 10px;
  }
  </style>
  