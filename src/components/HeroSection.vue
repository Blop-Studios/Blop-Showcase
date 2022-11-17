<template>
  <div class="flex justify-center items-center hero h-screen w-screen">
    <div class="text-[34vw] font-black font-display opacity-10 absolute z-10">
      BLOP
    </div>
    <div class="carousel w-screen h-[17rem] z-20">
      <swiper
        :modules="modules"
        :slides-per-view="3"
        :space-between="50"
        :mousewheel="true"
        :loop="true"
        class="h-full"
      >
        <swiper-slide>
          <div class="px-4 w-full h-full">
            <div class="bg-black swiper-content h-full w-full"></div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="px-4 w-full h-full">
            <div class="bg-black swiper-content h-full w-full"></div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="px-4 w-full h-full">
            <div class="bg-black swiper-content h-full w-full"></div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="px-4 w-full h-full">
            <div class="bg-black swiper-content h-full w-full"></div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="px-4 w-full h-full">
            <div class="bg-black swiper-content h-full w-full"></div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>
<script setup>
import { onMounted, ref } from "vue";
import { A11y, Mousewheel } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/mousewheel";

const modules = ref([A11y, Mousewheel]);
onMounted(() => {
  mousewheelListener();
});

function mousewheelListener() {
  document.addEventListener("wheel", (e) => {
    console.log(e);
    document.querySelectorAll(".swiper-content").forEach((el) => {
      el.style.borderRadius = "17% 83% 29% 71% / 100% 0% 100% 0%";
      setTimeout(() => {
        el.style.borderRadius = "0";
      }, 300);
    });
  });
}
</script>
<style>
.swiper-content {
  transition: all 0.2s linear;
}
</style>
