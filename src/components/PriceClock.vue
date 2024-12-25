<script setup>
import {computed, onMounted, ref} from 'vue'
import ClockNumber from "@/components/ClockNumber.vue";

const lastSecond = ref(0);
const activeSecond = ref(0);
const lastSecond10 = ref(0);
const activeSecond10 = ref(0);

const lastS = computed(() => lastSecond.value);
const currentS = computed(() => activeSecond.value);

const lastS10 = computed(() => lastSecond10.value);
const currentS10 = computed(() => activeSecond10.value);

const lastMinute = ref(0);
const activeMinute = ref(0);
const lastMinute10 = ref(0);
const activeMinute10 = ref(0);

const lastM = computed(() => lastMinute.value);
const currentM = computed(() => activeMinute.value);

const lastM10 = computed(() => lastMinute10.value);
const currentM10 = computed(() => activeMinute10.value);

function secondPlay() {

  const now = new Date()
  const seconds = now.getSeconds();

  const digits = String(seconds).split("").map(Number);
  let cs10 = 0;

  if (digits.length > 1) {
    cs10 = digits[0];
  }
  activeSecond10.value = cs10;
  lastSecond10.value = cs10 - 1;

  const cS = digits[digits.length - 1];
  activeSecond.value = cS;
  lastSecond.value = cS - 1;


  const minutes = now.getMinutes();
  const mDigits = String(minutes).split("").map(Number);

  let cm10 = 0;

  if (mDigits.length > 1) {
    cm10 = mDigits[0];
  }
  activeMinute10.value = cm10;
  lastMinute10.value = cm10 - 1;

  const cM = mDigits[digits.length - 1];
  activeMinute.value = cM;
  lastMinute.value = cM - 1;

}

onMounted(() => {
  setInterval(() => {
    secondPlay()
  }, 1000);
})

</script>

<template>
  <div class="container play">

    <ul class="flip minute10Play">

      <ClockNumber
          v-for="number in 10"
          :key="number - 1"
          :clockNr="number - 1"
          :active="currentM10 === (number - 1)"
          :before="lastM10 === (number - 1)"
      />
    </ul>

    <ul class="flip minutePlay">

      <ClockNumber
          v-for="number in 10"
          :key="number - 1"
          :clockNr="number - 1"
          :active="currentM === (number - 1)"
          :before="lastM === (number - 1)"
      />
    </ul>

    <ul class="flip second10Play">
      <ClockNumber
        v-for="number in 10"
        :key="number - 1"
        :clockNr="number - 1"
        :active="currentS10 === (number - 1)"
        :before="lastS10 === (number - 1)"
      />
    </ul>

    <ul class="flip secondPlay">

      <ClockNumber
          v-for="number in 10"
          :key="number - 1"
          :clockNr="number - 1"
          :active="currentS === (number - 1)"
          :before="lastS === (number - 1)"
      />
    </ul>

  </div>
</template>

<style scoped>
/* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

ul {
  list-style: none
}

.container {
  text-align: center;
  /*
  position: absolute;
  left: 50%;
  top: 50%;
  width: 140px;
  height: 90px;
  margin: -45px 0 0 -70px;
  */
}

/* Skeleton */

.flip {
  position: relative;
  float: left;
  margin: 5px;
  width: 60px;
  height: 90px;
  font-size: 80px;
  font-weight: bold;
  line-height: 87px;
  border-radius: 6px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, .7);
}

</style>
