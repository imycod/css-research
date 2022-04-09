<script setup></script>

<template>
  <div class="bd">
    <div class="box">111</div>
  </div>
</template>

<style lang="scss">
@import "node_modules/mathsass/dist/_math";

.bd {
  border: 1px solid #ccc;
}

@function spring-wobbly($t) {
  @return -0.5 * pow(2.71828, (-6 * $t)) *
    (-2 * pow(2.71828, (6 * $t)) + sin(12 * $t) + 2 * cos(12 * $t));
}
@function lerp($a, $b, $p) {
  @return $a + $p * ($b - $a);
}
@keyframes move {
  @for $i from 0 through 100 {
    #{$i}% {
      left: lerp(100px, 200px, spring-wobbly(calc($i/100)));
    }
  }
}
.box {
  animation: 1s move linear infinite;
  position: relative;
  background: red;
  width: 100px;
  height: 100px;
}
</style>
