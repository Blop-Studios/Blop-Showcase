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
        <swiper-slide v-for="project in projects" :key="project.title">
          <div class="px-4 w-full h-full">
            <div
              class="swiper-content h-full w-full bg-center bg-cover rounded-lg shadow-lg"
              :style="{ backgroundImage: `url(${project.image})` }"
            ></div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>

  <div
    class="absolute bottom-0 right-0 bg-black text-white text-2xl px-4 py-4 font-semibold"
  >
    Swipe or scroll to toggle through
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

const projects = ref([
  {
    title: "Godwin",
    image: "https://i.ibb.co/gFKdmj8/Screenshot-from-2022-10-30-10-08-13.png",
  },
  {
    title: "Amelia",
    image: "https://i.ibb.co/c3dQrvv/Screenshot-from-2022-10-30-10-28-53.png",
  },
  {
    title: "Afrobeats",
    image: "https://i.ibb.co/thzy4BS/Screenshot-from-2022-11-18-00-11-45.png",
  },
  {
    title: "Vinyl Fever",
    image: "https://i.ibb.co/47gPRsr/Screenshot-from-2022-11-18-00-14-21.png",
  },
  {
    title: "Yemisi",
    image: "https://i.ibb.co/5rv92y6/Screenshot-from-2022-10-31-16-00-20.png",
  },
]);

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
