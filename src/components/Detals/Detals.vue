<template>
    <div class="max-w-screen-xl m-auto">
        <div>
            <h1 class="text-center my-14 font-serif text-4xl">
                Детали
            </h1>
            <p class="flex justify-center font-serif mx-14 text-gray-600 text-[18px] text-center">
                Мы будем рады вашему присутствию на нашем празднике. В качестве подарков мы будем благодарны за:
            </p>
            <span class="flex justify-center font-serif mx-14 my-8 text-black text-[28px]">
                ***
            </span>
            <p class="flex justify-center font-serif mx-14 text-gray-600 text-[18px] text-center">
                • Книги <br>
                • Напитки <br>
                • Канцелярские товары, <br> которые будут переданы в больницу детям, и мы будем счастливы, если вы
                присоединитесь к нашему желанию принести радость и поддержку маленьким пациентам.
            </p>
            <p class="wave-text flex justify-center font-serif mx-14 text-gray-600 text-[18px] mt-5">
                <span v-for="(char, index) in waveText" :key="index" class="wave-char">{{ char }}</span>
            </p>
        </div>
        <div class="flex justify-center mt-20">
            <span class="w-[640px] mb-6 h-[1px] bg-gray-300 inline-block text-center clip-path-arrow"></span>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
const waveText = ref('Спасибо за ваше понимание и доброту!'.split(''));
</script>

<style scoped>
.wave-text {
  display: flex;
  justify-content: center;
}

.wave-char {
  display: inline-block;
  animation: wave 2.5s infinite;
  animation-delay: calc(var(--i) * 0.1s);
}

.wave-char:nth-child(1) { --i: 0; }
.wave-char:nth-child(2) { --i: 1; }
.wave-char:nth-child(3) { --i: 2; }
.wave-char:nth-child(4) { --i: 3; }
.wave-char:nth-child(5) { --i: 4; }
.wave-char:nth-child(6) { --i: 5; }
.wave-char:nth-child(7) { --i: 6; }
.wave-char:nth-child(8) { --i: 7; }
.wave-char:nth-child(9) { --i: 8; }
.wave-char:nth-child(10) { --i: 9; }
.wave-char:nth-child(11) { --i: 10; }
.wave-char:nth-child(12) { --i: 11; }
.wave-char:nth-child(13) { --i: 12; }
.wave-char:nth-child(14) { --i: 13; }
.wave-char:nth-child(15) { --i: 14; }
.wave-char:nth-child(16) { --i: 15; }
.wave-char:nth-child(17) { --i: 16; }
.wave-char:nth-child(18) { --i: 17; }
.wave-char:nth-child(19) { --i: 18; }
.wave-char:nth-child(20) { --i: 19; }
.wave-char:nth-child(21) { --i: 20; }
.wave-char:nth-child(22) { --i: 21; }
.wave-char:nth-child(23) { --i: 22; }
.wave-char:nth-child(24) { --i: 23; }
.wave-char:nth-child(25) { --i: 24; }
.wave-char:nth-child(26) { --i: 25; }
.wave-char:nth-child(27) { --i: 26; }
.wave-char:nth-child(28) { --i: 27; }
.wave-char:nth-child(29) { --i: 28; }
.wave-char:nth-child(30) { --i: 29; }
.wave-char:nth-child(31) { --i: 30; }
.wave-char:nth-child(32) { --i: 31; }
.wave-char:nth-child(33) { --i: 32; }
.wave-char:nth-child(34) { --i: 33; }
.wave-char:nth-child(35) { --i: 34; }
.wave-char:nth-child(36) { --i: 35; }
.wave-char:nth-child(37) { --i: 36; }
.wave-char:nth-child(38) { --i: 37; }
.wave-char:nth-child(39) { --i: 38; }
.wave-char:nth-child(40) { --i: 39; }
.wave-char:nth-child(41) { --i: 40; }
.wave-char:nth-child(42) { --i: 41; }
.wave-char:nth-child(43) { --i: 42; }
.wave-char:nth-child(44) { --i: 43; }
.wave-char:nth-child(45) { --i: 44; }
.wave-char:nth-child(46) { --i: 45; }

@keyframes wave {
  0%, 60%, 100% {
    transform: translateY(0);
  }
  30% {
    transform: translateY(-10px);
  }
}
</style>