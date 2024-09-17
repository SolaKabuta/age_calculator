<script setup lang="ts">
//import { RouterLink, RouterView } from 'vue-router'

import {ref, computed} from "vue";


const dayData = ref('')
const monthData = ref('')
const yearData = ref('')

const now = new Date();
const day = now.getDay(); // returns a number representing the day of the week, starting with 0 for Sunday
const month = now.getMonth();
const year = now.getFullYear();
console.log(`date ${day} / ${month} / ${year}`);

const blank = "- -"


const actualYear = computed(() => {
  const actualYear = (year - yearData.value)

  return actualYear
})

const actualMonth = computed(() => {
  const actualMonth = (month - monthData.value)

  return actualMonth
})

const actualDay = computed(() => {
  const actualDay = (day - dayData.value)

  return actualDay
})

</script>

<template>
  <main class="bg-Off_white w-screen h-screen grid place-content-center font-bold">
    <section class="bg-white w-[800px] h-[600px] rounded-3xl rounded-br-[30%] px-10 py-10">
      <div class="flex uppercase [&_label]:text-xs [&_div]:flex [&_div]:flex-col [&_input]:border [&_input]:border-Off_white [&_input]:px-6 [&_input]:py-2 [&_input]:my-2 [&_input]:w-3/4 [&_input]:rounded-md [&_input]:text-[32px]">
          <div>
            <label>Day</label>
            <input class="" type="text" v-model="dayData">
          </div>
          <div>
            <label>month</label>
            <input type="text" v-model="monthData">
          </div>
          <div>
            <label>year</label>
            <input type="text" v-model="yearData">
          </div>
      </div>

      <!--DIVIDER-->
      <div class="flex">
        <div class="bg-Off_white w-full h-[1px] my-10"></div>
        <button class="bg-Purple w-[90px] h-[80px] rounded-full grid place-content-center"><img src="@/assets/images/icon-arrow.svg" alt="arrow icon" width="46" height="44"></button>
      </div>

      <!--RESULT-->
      <div class="[&_p]:text-8xl [&_p_span]:text-Purple [&_p_span]:px-2 [&_p]:text-black">
      <p><span>{{ blank }}{{ actualYear }}</span>years</p>
      <p><span>{{ blank }}{{ actualMonth }}</span>months</p>
      <p><span>{{ blank }}{{ actualDay }}</span>days</p>
      </div>

    </section>
  </main>
</template>

<style scoped>

</style>
