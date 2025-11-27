<template lang="">
     <div class="flex justify-center mt-[200px] w-full ">
          <div class="bg-[#101828] block lg:min-w-[500px] min-w-96 p-6 border border-[#1e2939] rounded-md shadow-xs">

               <p v-if="flashcard =='' " class="text-center text-xl lg:text-3xl font-semibold text-white mt-5 capitalize">click next to display flashcard</p>
               <p v-else class="text-center text-3xl lg:text-5xl font-bold text-white mt-5 capitalize">{{flashcard?.romanji}}</p>
               <p v-if="show_answer" class="text-gray-500 text-xl text-center mt-2 ">{{flashcard?.answer}}</p>
               <div class="flex justify-between mt-12">
                    <button @click.prevent="show_answer = true" type="button" class="inline-flex items-center  text-white bg-brand hover:bg-brand-strong box-border border border-transparent focus:ring-4 focus:ring-brand-medium shadow-xs font-medium leading-5 rounded-base text-sm px-4 py-2.5 focus:outline-none">
                         Show
                         <Icon icon="solar:eye-scan-bold-duotone" class="text-2xl ml-1"/>
                    </button>
                    <button @click.prevent="next" type="button" class="inline-flex items-center  text-white bg-blue-700 hover:bg-blue-800 transition 
                    box-border border border-transparent focus:ring-4 focus:ring-brand-medium 
                    shadow-xs font-medium leading-5 rounded-md text-sm px-4 py-2.5 focus:outline-none">
                         Next
                    <svg class="w-4 h-4 ms-1.5 -me-0.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 12H5m14 0-4 4m4-4-4-4"/>
                    </svg>
                    </button>
               </div>
          </div>
     </div>
</template>
<script setup>
import { Icon } from "@iconify/vue";
import image from "@/assets/logo.svg";
import japaneseWords from "./data";
import { ref } from "vue";
const flashcard = ref("");
const show_answer = ref(false);
const next = () => {
     show_answer.value = false;
     const random = Math.random();
     const min = 1;
     const max = japaneseWords.length;
     const index = Math.floor(Math.random() * max) + 1;
     flashcard.value = japaneseWords[index - 1];
     japaneseWords.splice(index-1,1);
     console.log(max)

}
</script>
<style lang="">
     
</style>