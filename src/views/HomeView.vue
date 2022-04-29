<script setup lang="ts">
import { ref } from "vue";
import dayjs from "dayjs";
import relativeTime from "dayjs/plugin/relativeTime";
dayjs.extend(relativeTime);
const shamin = ref<"work" | "relaxed">("work");
const toggleShamin = () => {
  shamin.value = shamin.value === "work" ? "relaxed" : "work";
};
const festival = dayjs("2022-05-17");
const festivalCountdown = dayjs().to(festival, true);

const deadline = dayjs("2022-04-29 18:00");
const deadlineCountdown = dayjs().to(deadline, true);
</script>

<template>
  <div class="flex h-full">
    <div class="w-1/5 grid grid-rows-4">
      <div
        class="bg-neutral-600 text-white flex flex-row items-center relative"
      >
        <p class="font-bold text-9xl text-center w-full">
          {{ festivalCountdown.split(" ")[0]
          }}<span class="text-base font-normal">{{
            festivalCountdown.split(" ")[1]
          }}</span>
        </p>
        <p class="text-right right-8 bottom-8 absolute flex">
          <span>until the</span>
          <img src="/src/assets/images/omr-logo.svg" alt="" class="h-8 mx-2" />
          <span> festival</span>
        </p>
      </div>
      <div
        class="bg-neutral-300 text-black flex flex-row items-center relative"
      >
        <p class="font-bold text-9xl text-center w-full">
          {{ deadlineCountdown.split(" ")[0]
          }}<span class="text-base font-normal">{{
            deadlineCountdown.split(" ")[1]
          }}</span>
        </p>

        <p class="text-right right-8 bottom-8 absolute flex">
          <span>until the MVP APP deadline</span>
        </p>
      </div>
      <div
        class="row-span-2"
        @click="toggleShamin"
        style="background-position: center; background-size: cover"
        :style="{
          backgroundImage: `url('/src/assets/images/shamin-${shamin}.png')`,
        }"
      >
        <div class="font-bold p-4 text-lg">
          <p v-if="shamin === 'work'">shamin is in a call</p>
          <p v-else>shamin is available</p>
        </div>
      </div>
    </div>
    <div class="grid grid-rows-4">
      <div>top</div>
      <div class="row-span-3">bottom</div>
    </div>
  </div>
</template>
