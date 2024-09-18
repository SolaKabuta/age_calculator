<script setup lang="ts">
//import { RouterLink, RouterView } from 'vue-router'

import {ref} from "vue";


const dayData = ref('')
const monthData = ref('')
const yearData = ref('')

const now = new Date();
const day = now.getDay() ; // returns a number representing the day of the week, starting with 0 for Sunday
const month = now.getMonth() +1;
const year = now.getFullYear();
console.log(`date ${day} / ${month} / ${year}`);

const isActive = ref(false)

const isRequired = ref(false)

const actualYear = ref('- -')
const actualMonth = ref('- -')
const actualDay = ref('- -')


function yearCount () {
  isActive.value = !isActive.value
  actualDay.value = (day - dayData.value)
  actualMonth.value = (month - monthData.value)
  actualYear.value = (year - yearData.value)
}

function stopCount () {
  if (isActive.value = !isActive.value || isNaN(dayData.value) ) {
    console.log('test not working') ;
  } else {
    console.log("test working")
  }
}

function handleCLick () {
  yearCount();
  stopCount()

}

function errorState () {
  let errorMessage = ref('not valid data')
  if (dayData.value > 31 || dayData.value < 1) {
    return errorMessage
  }
}

</script>

<template>
  <main class="bg-Off_white w-screen h-screen grid place-content-center font-bold">
    <section class="bg-white w-[800px] h-[600px] rounded-3xl rounded-br-[30%] px-10 py-10" >
      <div class="flex uppercase [&_label]:text-xs [&_div]:flex [&_div]:flex-col [&_input]:border [&_input]:border-Off_white [&_input]:px-6 [&_input]:py-2 [&_input]:my-2 [&_input]:w-3/4 [&_input]:rounded-md [&_input]:text-[32px]">
          <div>
            <label :class="{'text-red-600' : isNaN(actualDay) && isActive,}">Day</label>
            <input  class="" type="text" v-model="dayData">
            <transition name="fade">
            <p class="text-xs text-red-600 transition duration-500 ease-out" v-if="isActive = !isActive">Must be a valid day</p>
            </transition>
          </div>
          <div>
            <label>month</label>
            <input type="number" v-model="monthData">
          </div>
          <div>
            <label>year</label>
            <input type="number" v-model="yearData">
          </div>
      </div>

      <!--DIVIDER-->
      <div class="flex" @keyup.enter="toggleActive">
        <div class="bg-Off_white w-full h-[1px] my-10"></div>
        <button @click="handleCLick"  :class="{'bg-Purple' : !isActive, 'bg-black' : isActive}" class="transition duration-500 ease-out w-[90px] h-[80px] rounded-full grid place-content-center"><img src="@/assets/images/icon-arrow.svg" alt="arrow icon" width="46" height="44"></button>
      </div>

      <!--RESULT-->
      <div class="[&_p]:text-8xl [&_p_span]:text-Purple [&_p_span]:px-2 [&_p]:text-black">
      <p><span>{{ actualYear }}</span>years</p>
      <p><span>{{ actualMonth }}</span>months</p>
      <p><span>{{ actualDay }}</span>days</p>
      </div>

    </section>
  </main>
</template>

<style scoped>
/* Transition classes */
.fade-enter-active, .fade-leave-active {
  transition: opacity 1s ease-in-out;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
