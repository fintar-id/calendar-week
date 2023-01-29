<template>
  <div class="min-h-screen bg-gray-100">
    <div class="container px-4 md:px-0 mx-auto flex">
      <div class="py-4 flex mx-auto">
        <div class="flex flex-col space-y-2">
          <div class="bg-white rounded-lg p-4 flex justify-between">
            <div class="text-4xl md:text-6xl font-bold flex flex-col space-y-4">
              <p>Calendar</p>
              <p>Weeks</p>
              <p>OF {{ state.year }}</p>
            </div>
            <div class="text-2xl md:text-4xl font-bold mt-auto">
              <p>{{ state.week }} / {{ state.weeks }}</p>
            </div>
          </div>
          <div class="bg-white rounded-lg grid grid-cols-8 gap-2 pt-8">
            <div v-for="index in state.weeks">
              <div v-if="index <= state.week">
                <div class="md:hidden w-[55px]">
                  <svg viewBox="0 25 100 100">
                    <circle cx="50" cy="50" r="20" stroke="red" stroke-width="4" fill="white" fill-opacity="0"/>
                    <circle cx="50" cy="50" r="14" fill="red" fill-opacity="1"/>
                  </svg>
                </div>
                <div class="hidden md:block w-20">
                  <svg viewBox="0 25 100 100">
                    <circle cx="50" cy="50" r="20" stroke="red" stroke-width="4" fill="white" fill-opacity="0"/>
                    <circle cx="50" cy="50" r="14" fill="red" fill-opacity="1"/>
                  </svg>
                </div>
              </div>
              <div v-else>
                <div class="md:hidden w-[55px]">
                  <svg viewBox="0 25 100 100">
                    <circle cx="50" cy="50" r="20" stroke="black" stroke-width="4" fill="white" fill-opacity="0"/>
                  </svg>
                </div>
                <div class="hidden md:block w-20">
                  <svg viewBox="0 25 100 100">
                    <circle cx="50" cy="50" r="20" stroke="black" stroke-width="4" fill="white" fill-opacity="0"/>
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<script setup>
import {reactive} from "vue";
import moment from "moment/moment";

const state = reactive({
  year: new Date().getFullYear(),
  weeks: moment().isoWeeksInYear(),
  week: moment().isoWeek(),
})

</script>

<style scoped>

</style>