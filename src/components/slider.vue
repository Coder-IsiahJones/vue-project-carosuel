<style scoped>
.splide__slide {
  transform: scale(0.85);
}

.splide__slide.is-active {
  transform: scale(1);
}
.splide__pagination {
  background-color: red;
}
img {
  display: block;
  width: 100%;
  box-sizing: border-box;
}
</style>

<template>
  <div id="splide" class="splide">
    <div class="splide__track">
      <ul class="splide__list">
        <li class="splide__slide" v-for="img in images" :key="img">
          <img :src="img" alt="test" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Splide from "@splidejs/splide";
import { Intersection } from "@splidejs/splide-extension-intersection";
// Default theme
import "@splidejs/vue-splide/css";

// create a array of images in js
const images = [
  "https://cannonball-cdn.bamgrid.com/assets/originals/Poster_ArtemisFowl_EN_v2.jpg",
  "https://cannonball-cdn.bamgrid.com/assets/originals/poster-1@2x.png",
  "https://cannonball-cdn.bamgrid.com/assets/originals/The_Mandalorian_Key_Art_en-US.jpg",
  "https://cannonball-cdn.bamgrid.com/assets/originals/Star_Wars_Rise_Of_Skywalker_Grid_Item_with_BUG.png",
];

export default {
  name: "Slider",
  data() {
    return {
      images: images,
    };
  },
  created() {
    document.addEventListener("DOMContentLoaded", function () {
      new Splide(".splide", {
        type: "loop",
        perPage: 1,
        focus: "center",
        fixedWidth: "40%",
        rewind: false,
        drag: true,
        flickMaxPages: 2,
        updateOnMove: true,
        gap: "-2rem",
        arrows: false,
        interval: 10000,
        pauseOnHover: true,
        autoplay: "pause",
        intersection: {
          inView: {
            autoplay: true,
          },
        },
      }).mount({ Intersection });
    });
  },
};
</script>