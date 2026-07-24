<template>
  <div class="max-w-7xl m-center pt-20">
    <div class="about-me text-center mt-10 md:mt-32" data-aos="fade-up" data-aos-delay="100" data-aos-duration="800"><h2 class="text-5xl dark:text-white">Portfolio</h2><span class="f-gray text-sm dark:text-white">Recent Work</span></div>
    <div class="details flex gap-10 justify-center" data-aos="fade-left" data-aos-delay="500" data-aos-duration="600">
      <swiper
        :slidesPerView="3"
        :spaceBetween="0"
        :centeredSlides="false"
        :loop="true"
        :speed="850"
        :autoplay="{ delay: 2800, disableOnInteraction: false, pauseOnMouseEnter: true }"
        :pagination="{ clickable: true }"
        :modules="modules"
        :breakpoints="{ '200':{slidesPerView:1}, '600':{slidesPerView:2,spaceBetween:25}, '768':{slidesPerView:3} }"
        class="mySwiper"
      >
        <swiper-slide v-for="project in projects" :key="project.name">
          <div class="custom-card bg-white dark:bg-slate-800 drop-shadow-2xl w-full max-w-xs h-96 rounded">
            <div class="tools"><div class="circle"><span class="red box"></span></div><div class="circle"><span class="yellow box"></span></div><div class="circle"><span class="green box"></span></div></div>
            <div class="card__content p-5"><div class="project-details"><div class="project-mark">{{ project.mark }}</div><div class="title dark:text-white text-2xl font-semibold">{{ project.name }}</div><div class="description text-sm text-gray-400">{{ project.description }}</div></div><div class="tech-list"><span v-for="tech in project.tech" :key="tech" class="tech">{{ tech }}</span></div></div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>
<script lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue"; import "swiper/css"; import "swiper/css/pagination"; import { Autoplay, Pagination } from "swiper";
export default { components:{Swiper,SwiperSlide}, setup(){return{modules:[Autoplay,Pagination]}}, data(){return{projects:[
  {mark:"IMS",name:"Inventory Management System",description:"A municipal system for organizing inventory records, monitoring items, and supporting day-to-day inventory operations.",tech:["PHP","CodeIgniter","MySQL"]},
  {mark:"LBMS",name:"Local Budget Management System",description:"A web-based solution supporting local budget records, workflows, and municipal financial administration.",tech:["PHP","JavaScript","PostgreSQL"]},
  {mark:"BPC",name:"Business Permit & Clearance",description:"Frontend development for municipal business permit and clearance services in the Municipality of Baras.",tech:["HTML5","CSS3","Bootstrap"]},
  {mark:"BMS",name:"Barangay Management System",description:"A freelance information system designed to support barangay records and administrative workflows.",tech:["CodeIgniter","JavaScript","MySQL"]},
  {mark:"DRMS",name:"DRMS",description:"A freelance records management system with structured data workflows, administrative tools, and database support.",tech:["PHP","REST API","SQL"]},
  {mark:"SMS",name:"School Management System",description:"A freelance web application supporting school information, records, and administrative processes.",tech:["PHP","Bootstrap","MySQL"]}
]}} };
</script>
<style scoped>
.custom-card{box-sizing:border-box;border-radius:8px;z-index:1;height:26rem!important;min-height:26rem;max-height:26rem;overflow:hidden}.tools{display:flex;align-items:center;height:2.5rem;padding:9px}.circle{padding:0 4px}.box{display:inline-block;width:10px;height:10px;padding:1px;border-radius:50%}.red{background:#ff605c}.yellow{background:#ffbd44}.green{background:#00ca4e}.swiper{width:100%;height:65vh;overflow:hidden}.swiper :deep(.swiper-wrapper){align-items:center}.swiper-slide{text-align:center;font-size:18px;display:flex;justify-content:center;align-items:center;align-self:center;min-width:0;height:26rem!important}.card__content{height:23.5rem;min-width:0;display:grid;grid-template-rows:1fr 3.25rem;gap:.5rem}.project-details{display:grid;grid-template-rows:8rem 3.75rem 5rem;gap:.5rem;align-content:start}.title{height:3.75rem;display:flex;align-items:center;justify-content:center;line-height:1.2;overflow:hidden}.description{height:5rem;display:-webkit-box;-webkit-box-orient:vertical;-webkit-line-clamp:4;overflow:hidden;line-height:1.35}.project-mark{width:7rem;height:7rem;margin:.25rem auto .75rem;display:grid;place-items:center;border-radius:1.25rem;background:rgba(37,99,235,.1);color:#2563eb;font-size:1.5rem;font-weight:800}.tech-list{height:3.25rem;display:flex;flex-wrap:wrap;align-content:center;align-items:center;justify-content:center;gap:.5rem;overflow:hidden}.tech{padding:.3rem .55rem;border-radius:999px;background:rgba(37,99,235,.1);color:#2563eb;font-size:.7rem}
.swiper :deep(.swiper-slide){height:26rem!important;min-height:26rem;max-height:26rem;display:flex;align-items:center;align-self:center}
</style>
