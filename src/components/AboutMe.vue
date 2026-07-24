<template>
  <div class="max-w-7xl m-center pt-20 pb-20">
    <div class="about-me text-center mt-10 md:mt-32" data-aos="fade-up" data-aos-delay="100" data-aos-duration="800">
      <h2 class="text-5xl dark:text-white">About Me</h2><span class="f-gray text-sm dark:text-white">Personal</span>
    </div>
    <div class="details flex mt-20 md:flex-col-reverse lg:flex-row lg:items-start flex-col-reverse">
      <div class="image lg:w-3/6 mt-12 lg:mt-0 lg:pr-12" data-aos="fade-right" data-aos-delay="500" data-aos-duration="500">
        <div class="image-card w-11/12 m-auto lg:m-0">
          <img class="w-full rounded-md" :src="`${imageBase}imgs/raf_bg.jpg`" alt="Rafael Cawicaan" />
          <span class="image-card__shine" aria-hidden="true"></span>
        </div>
      </div>
      <div class="information lg:w-3/6 flex flex-col" data-aos="fade-right" data-aos-delay="1200" data-aos-duration="500">
        <div class="cover-letter f-gray text-lg pb-7 dark:text-white text-center lg:text-left md:justify-center lg:justify-start">
          Web Developer with over 3 years of professional experience developing and maintaining web applications and municipal information systems. As a tech-savvy Virtual Assistant, I can also support clients with Canva editing, data entry, web research, document preparation, email and file organization, customer support, and other day-to-day digital tasks. I am detail-oriented, organized, adaptable, and committed to clear communication, confidentiality, accuracy, and dependable delivery.
        </div>
        <div class="summary-experience flex text-center justify-center lg:justify-start">
          <div class="years-exp mr-5 w-2/12"><h2 class="text-3xl f-dark-blue font-extrabold dark:text-blue-500">3+</h2><span class="text-sm f-gray dark:text-white">Years of Experience</span></div>
          <div class="projects mr-5 w-2/12"><h2 class="text-3xl f-dark-blue font-extrabold dark:text-blue-500">6</h2><span class="text-sm f-gray dark:text-white">Featured Systems</span></div>
          <div class="companies-worked mr-5 w-2/12"><h2 class="text-3xl f-dark-blue font-extrabold dark:text-blue-500">2-in-1</h2><span class="text-sm f-gray dark:text-white">Developer & VA Support</span></div>
        </div>
        <div class="resume pt-10"><button class="btn-accent flex items-center m-auto lg:m-0"><a :href="resumeUrl" target="_blank">Download CV&nbsp;<font-awesome-icon class="w-4" :icon="['fas', 'arrow-circle-down']" /></a></button></div>
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
const imageBase = import.meta.env.BASE_URL;
const resumeUrl = `${imageBase}Rafael-Cawicaan-Resume.pdf`;
</script>

<style lang="scss" scoped>
.image {
  perspective: 1100px;
}

.image-card {
  position: relative;
  overflow: hidden;
  border-radius: 0.75rem;
  box-shadow: 0 20px 45px rgba(15, 23, 42, 0.18);
  transform-style: preserve-3d;
  transform: rotateX(0deg) rotateY(0deg) translateY(0);
  transition: transform 650ms cubic-bezier(0.22, 1, 0.36, 1),
    box-shadow 650ms cubic-bezier(0.22, 1, 0.36, 1);

  img {
    display: block;
    aspect-ratio: 16 / 10;
    object-fit: cover;
    transition: transform 750ms cubic-bezier(0.22, 1, 0.36, 1),
      filter 500ms ease;
  }

  &::after {
    content: "";
    position: absolute;
    inset: 0;
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: inherit;
    pointer-events: none;
  }

  &:hover {
    transform: rotateX(4deg) rotateY(-7deg) translateY(-10px) scale(1.02);
    box-shadow: 18px 28px 55px rgba(15, 23, 42, 0.28);

    img {
      transform: scale(1.06) translateZ(24px);
      filter: saturate(1.08) contrast(1.03);
    }

    .image-card__shine {
      opacity: 1;
      transform: translateX(65%) rotate(18deg);
    }
  }
}

.image-card__shine {
  position: absolute;
  top: -35%;
  left: -70%;
  width: 45%;
  height: 175%;
  opacity: 0;
  pointer-events: none;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.28), transparent);
  transform: translateX(0) rotate(18deg);
  transition: transform 850ms ease, opacity 300ms ease;
}

@media (prefers-reduced-motion: reduce) {
  .image-card,
  .image-card img,
  .image-card__shine {
    transition-duration: 0.01ms;
  }
}
</style>
