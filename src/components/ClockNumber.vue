<script setup>
import {defineProps} from 'vue'

const props = defineProps({
  clockNr: Number,
  active: Boolean,
  before: Boolean,
})

</script>

<template>
  <li :class="{
        active: props.active,
        before: props.before,
      }"
  >
    <div class="up">
      <div class="shadow"></div>
      <div class="inn">{{ props.clockNr }}</div>
    </div>
    <div class="down">
      <div class="shadow"></div>
      <div class="inn">{{ props.clockNr }}</div>
    </div>
  </li>

</template>

<style scoped>
/* Reset */

li {
  cursor: pointer;
  text-decoration: none;
  color: #ccc;
}

li:hover {
  color: #fff;
}


li {
  z-index: 1;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;

}

li:first-child {
  z-index: 2;
}

li {
  display: block;
  height: 100%;
  perspective: 200px;
}

li div {
  z-index: 1;
  position: absolute;
  left: 0;
  width: 100%;
  height: 50%;
  overflow: hidden;
}

li div .shadow {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 2;
}

li div.up {
  transform-origin: 50% 100%;
  top: 0;
}

li div.up:after {
  content: "";
  position:absolute;
  top:44px;
  left:0;
  z-index: 5;
  width: 100%;
  height: 3px;
  background-color: rgba(0,0,0,.4);
}

li div.down {
  transform-origin: 50% 0%;
  bottom: 0;
}

li div div.inn {
  position: absolute;
  left: 0;
  z-index: 1;
  width: 100%;
  height: 200%;
  color: #ccc;
  text-shadow: 0 1px 2px #000;
  text-align: center;
  background-color: #333;
  border-radius: 6px;
}

li div.up div.inn {
  top: 0;

}

li div.down div.inn {
  bottom: 0;
}

/* PLAY */

li.before {
  z-index: 3;
}

li.active {
  animation: asd .5s .5s linear both;
  z-index: 2;
}

@keyframes asd {
  0% {
    z-index: 2;
  }
  5% {
    z-index: 4;
  }
  100% {
    z-index: 4;
  }
}

li.active .down {
  z-index: 2;
  animation: turn .5s .5s linear both;
}

@keyframes turn {
  0% {
    transform: rotateX(90deg);
  }
  100% {
    transform: rotateX(0deg);
  }
}

li.before .up {
  z-index: 2;
  animation: turn2 .5s linear both;
}

@keyframes turn2 {
  0% {
    transform: rotateX(0deg);
  }
  100% {
    transform: rotateX(-90deg);
  }
}

/* SHADOW */

li.before .up .shadow {
  background: -moz-linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, rgba(0, 0, 0, .1)), color-stop(100%, rgba(0, 0, 0, 1)));
  background: linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: -o-linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: -ms-linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: linear-gradient(to bottom, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  animation: show .5s linear both;
}

li.active .up .shadow {
  background: -moz-linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, rgba(0, 0, 0, .1)), color-stop(100%, rgba(0, 0, 0, 1)));
  background: linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: -o-linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: -ms-linear-gradient(top, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  background: linear-gradient(to bottom, rgba(0, 0, 0, .1) 0%, rgba(0, 0, 0, 1) 100%);
  animation: hide .5s .3s linear both;
}

/*DOWN*/

li.before .down .shadow {
  background: -moz-linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, rgba(0, 0, 0, 1)), color-stop(100%, rgba(0, 0, 0, .1)));
  background: linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: -o-linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: -ms-linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: linear-gradient(to bottom, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  animation: show .5s linear both;
}

li.active .down .shadow {
  background: -moz-linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0%, rgba(0, 0, 0, 1)), color-stop(100%, rgba(0, 0, 0, .1)));
  background: linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: -o-linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: -ms-linear-gradient(top, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  background: linear-gradient(to bottom, rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, .1) 100%);
  animation: hide .5s .3s linear both;
}

@keyframes show {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes hide {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>
