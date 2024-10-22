<template>
  <div class="relative mx-auto overflow-hidden">
    <NuxtImg
      width="1400"
      height="800"
      class="object-cover w-full h-[420px] lg:h-[560px] xl:h-[640px]"
      src="/images/hero.jpg"
      alt="Hero image"
      loading="eager"
      sizes="sm:100vw md:1400px"
      fetchpriority="high"
      preload
      placeholder
      placeholder-class="blur-xl"
      :style="{ transform: `translateY(${offset * 0.3}px)` }"
    />
    <div
      class="container absolute inset-0 flex flex-col items-start justify-center bg-gradient-to-l  text-white"
    >
      <h1 class="text-3xl font-bold md:mb-4 md:text-4xl lg:text-6xl">
        A bearanyozott <br />pillanatokért
      </h1>
      <div class="max-w-sm mb-8 text-md font-light lg:max-w-md text-balance">
        <p>
          Fedezd fel gondosan válogatott kínálatunkat, és találd meg a
          hangulatodhoz illő tökéletes teát.
        </p>
      </div>
      <NuxtLink
        to="#"
        class="group relative inline-block overflow-hidden bg-gold px-8 py-3 text-white rounded-full transition-all duration-300 ease-out hover:bg-[#C69362]"
      >
        <span
          class="absolute right-0 w-8 h-32 -mt-12 transition-all duration-1000 transform translate-x-12 bg-white opacity-10 rotate-12 group-hover:-translate-x-40 ease"
        ></span>
        <span class="relative text-xl font-semibold tracking-wider">
          Kínálatunk
        </span>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const offset = ref(0)

const handleScroll = () => {
  offset.value = window.pageYOffset
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
@keyframes wave {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 100% 0;
  }
}

.container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 24px;
  background-image: url('/images/wave-pattern.png');
  background-size: 24px 24px;
  animation: wave 10s linear infinite;
  opacity: 0.5;
}
</style>