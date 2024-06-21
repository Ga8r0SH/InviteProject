<template>
  <div class="flex items-center justify-center h-screen">
    <div class="content relative w-full h-full">
      <img src="../../assets/Image/photo_2024-06-19_20-57-31.jpg" alt="Example Image" class="image" />
      <div class="absolute inset-0 flex items-center justify-center bg-black bg-opacity-50">
        <div class="text-white text-center px-4 font-serif">
          <span class="block text-6xl mt-12 mb-3">Дорогие гости!</span>
          <span class="block text-xl mt-12">В нашей жизни предстоят счастливые перемены! Мы хотим, чтобы в этот
            день рядом с нами были самые близкие и дорогие для нас люди. Будем
            рады разделить с вами чудесный праздник в день нашей свадьбы.</span>
          <span class="font-bold block my-8 text-xl">7 Сентября 2024 года</span>
          <span class="block mt-4 text-xl">С любовью, София и Александр</span>
          <div class="countdown-container mt-4">
            <div class="countdown-label text-sm mt-4">До свадьбы осталось:</div>
            <div class="countdown-timer mt-8">
              <div class="time text-2xl">{{ countdown.days }}<span>дней</span></div>
              <div class="separator">|</div>
              <div class="time text-2xl">{{ countdown.hours }}<span>часов</span></div>
              <div class="separator">|</div>
              <div class="time text-2xl">{{ countdown.minutes }}<span>минут</span></div>
              <div class="separator">|</div>
              <div class="time text-2xl">{{ countdown.seconds }}<span>секунд</span></div>
            </div>
          </div>
          <div class="button flex justify-center items-center my-12">
            <button class="animated-button"><span class="textanimation">Перейти к приглашению</span></button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  name: 'WeddingCountdown',
  setup() {
    const countdown = ref({
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
    });

    onMounted(() => {
      const weddingDate = new Date('September 7, 2024 19:00:00').getTime();
      const updateCountdown = () => {
        const now = new Date().getTime();
        const distance = weddingDate - now;
        countdown.value.days = Math.floor(distance / (1000 * 60 * 60 * 24));
        countdown.value.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        countdown.value.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        countdown.value.seconds = Math.floor((distance % (1000 * 60)) / 1000);
      };
      updateCountdown();
      const intervalId = setInterval(updateCountdown, 1000);
      return () => clearInterval(intervalId);
    });

    return {
      countdown,
    };
  },
};
</script>

<style scoped>
.animated-button {
  position: relative;
  margin-top: 30px;
  padding: 10px 25px;
  font-size: 18px;
  color: white;
  background: linear-gradient(to right, rgba(240, 237, 237, 0.527) 0%, rgba(221, 219, 219, 0.192) 50%, rgba(235, 232, 232, 0.521) 100%);
  border: none;
  cursor: pointer;
  overflow: hidden;
  transition: color 0.4s;
}

.animated-button::before, .animated-button::after {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
  background: linear-gradient(to right, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.2) 10%, rgba(255, 255, 255, 0.4) 50%, rgba(255, 255, 255, 0.2) 90%, rgba(255, 255, 255, 0) 100%);
  transition: all 0.5s ease-in-out;
}

.animated-button:hover {
  background-color: black;
  color: white;
}

.animated-button::before {
  left: -100%;
}

.animated-button::after {
  right: -100%;
}

.animated-button:hover::before, .animated-button:hover::after {
  left: 100%;
  right: 100%;
}

.textanimation {
  position: relative;
  display: inline-block;
}

.textanimation:hover {
  animation: bounce 0.5s ease infinite alternate;
}

@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-3px);
  }
}

.content {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.5);
}

.countdown-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.countdown-label {
  font-size: 1rem;
}

.countdown-timer {
  display: flex;
  align-items: center;
  font-size: 2rem;
}

.time {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.separator {
  margin: 0 0.5rem;
  font-size: 25px;
}

/* Responsive styles */
@media (max-width: 768px) {
  .animated-button{
    display: block;
  }
  .text-white {
    padding: 1rem;
  }

  .text-6xl {
    font-size: 2.5rem;
  }

  .text-xl {
    font-size: 1rem;
  }

  .countdown-timer {
    font-size: 1.5rem;
  }
}
</style>

