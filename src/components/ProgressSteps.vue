<template>


   <div 
   class="w-[500px] max-[500px]:w-[95%] mx-auto flex flex-row border border-gray-500  rounded shadow-lg ">
        
       <div class="flex-1 border-r p-2" :class="{'bg-blue-700 text-white font-bold': index === currentStep}"  v-for="(step, index) in steps" :key="index" >
        <span class="w-full"  >{{ step }}</span>

       </div>
        
   </div>

   <div class="mx-auto w-max mt-5  space-x-3">
        <button :disabled="currentStep === 0" class="border disabled:opacity-50 disabled:cursor-not-allowed max-[300px]:text-sm max-[300px]:p-2 p-3 rounded-lg cursor-pointer bg-red-600 hover:bg-red-800 text-white font-bold" @click="previousStep">Previous Step</button>
        <button :disabled="currentStep === steps.length - 1" class="border disabled:opacity-50 disabled:cursor-not-allowed max-[300px]:text-sm max-[300px]:py-2 max-[300px]:px-4 py-3 px-7 rounded-lg cursor-pointer bg-green-600 hover:bg-green-800 text-white font-bold " @click="nextStep">Next Step</button>
   </div>

</template>


<script setup>
   import {ref} from 'vue'

   const steps = ref(['Step 1', 'Step 2', 'Step 3']) //its index is 0,1,2 while the length is 3
   const currentStep = ref(0)

   const nextStep = () => {
       if (currentStep.value < steps.value.length - 1 ) {    // minus 1 because length is more than the index by 1
          currentStep.value++
       }
   }

   const previousStep = () => {
    if (currentStep.value > 0) {
        currentStep.value--
    }
   }


</script>