<template>
    <div>
      <component :is="currentStepComponent" :step="currentStep" @next-step="onNextStep"></component>
      <div v-if="errorMessage" class="error">{{errorMessage}}</div>
    </div>
  </template>
  
  <script lang="ts">
  import Paso1 from './StepOne.vue';
  import Paso2 from './StepTwo.vue';
  import Paso3 from './StepThree.vue';
  
  export default {
    components: {
      Paso1,
      Paso2,
      Paso3
    },
    data() {
      return {
        currentStep: 1,
        errorMessage: null,
        formData: {}
      }
    },
    computed: {
      currentStepComponent() {
        return 'Paso' + this.currentStep;
      }
    },
    methods: {
      onNextStep(data) {
        this.formData = { ...this.formData, ...data };
        this.errorMessage = null;
        if (this.currentStep < 3) {
          this.currentStep++;
        } else {
          // Submit the form data
          console.log(this.formData);
        }
      }
    }
  }
  </script>