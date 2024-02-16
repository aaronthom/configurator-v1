<template>
    <div class="checkbox-matrix">
      <!-- Erstellt eine Reihe von Checkboxen basierend auf numCheckboxes -->
      <div class="checkbox-row" v-for="index in numCheckboxes" :key="index">
        <input type="checkbox" id="checkbox-{{ index }}" :value="index" />
        <label for="checkbox-{{ index }}"> {{ index }}</label>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      numCheckboxes: {
        type: Number,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  .checkbox-matrix {
    display: flex;
    flex-direction: row;
  }
  
  .checkbox-row {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
  }
  
  input[type='checkbox'] {
    margin-right: 5px;
  }
  </style>