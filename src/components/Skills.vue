<template>
  <div class="max-w-7xl m-center pt-48">
    <div class="skills text-center mt-10" data-aos="fade-up" data-aos-delay="100" data-aos-duration="800"><h2 class="text-5xl dark:text-white">Skills</h2><span class="f-gray text-sm dark:text-white">My Technical Level</span></div>
    <div class="skill-details flex mt-20 flex-col lg:flex-row lg:gap-10">
      <div v-for="(group, index) in groups" :key="group.title" data-aos="fade-down" data-aos-duration="1000" :data-aos-delay="200 + index * 200" class="lg:w-1/3 md:w-96 md:m-auto md:mb-16 card bg-white drop-shadow-2xl dark:bg-slate-800">
        <h2 class="pt-7 pl-5 flex items-center"><font-awesome-icon class="fa-2xl pr-3 f-blue w-20" :icon="['fas', group.icon]" /><div class="flex flex-col"><h2 class="text-xl dark:text-white">{{ group.title }}</h2><span class="text-sm f-gray dark:text-white">{{ group.subtitle }}</span></div></h2>
        <div class="description grid grid-cols-4 gap-4 m-auto lg:px-10 px-5 pt-10">
          <div v-for="skill in group.skills" :key="skill.name" class="p-1 card-mini">
            <img v-if="skill.icon" :src="skill.icon" :alt="`${skill.name} logo`" class="skill-icon" loading="lazy" />
            <div v-else class="skill-icon skill-icon--service"><font-awesome-icon :icon="['fas', skill.fa]" /></div>
            <span class="dark:text-white">{{ skill.name }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
type Skill = { name: string; icon?: string; fa?: string };
type SkillGroup = { title: string; subtitle: string; icon: string; skills: Skill[] };

const groups: SkillGroup[] = [
  { title: "Frontend Development", subtitle: "Responsive web interfaces", icon: "code", skills: [
    { name: "JavaScript", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" },
    { name: "HTML5", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" },
    { name: "CSS3", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" },
    { name: "Bootstrap", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bootstrap/bootstrap-original.svg" },
    { name: "jQuery", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/jquery/jquery-original.svg" },
    { name: "Responsive", fa: "mobile-screen" },
    { name: "Vue.js", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vuejs/vuejs-original.svg" },
    { name: "Angular", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/angular/angular-original.svg" },
  ] },
  { title: "Backend Development", subtitle: "3+ years of experience", icon: "code-branch", skills: [
    { name: "PHP", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/php/php-original.svg" },
    { name: "CodeIgniter", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/codeigniter/codeigniter-plain.svg" },
    { name: "REST API", fa: "plug" },
    { name: "MySQL", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg" },
    { name: "PostgreSQL", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original.svg" },
    { name: "SQL", fa: "database" },
    { name: "MVC", fa: "sitemap" },
    { name: "Python", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" },
    { name: "Django", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/django/django-plain.svg" },
    { name: "Flask", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/flask/flask-original.svg" },
  ] },
  { title: "Virtual Assistance", subtitle: "Creative & administrative support", icon: "brain", skills: [
    { name: "Canva Editing", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/canva/canva-original.svg" },
    { name: "Graphic Content", fa: "palette" },
    { name: "Social Media Posts", fa: "share-nodes" },
    { name: "Presentation Design", fa: "display" },
    { name: "Basic Photo Editing", fa: "image" },
    { name: "Content Scheduling", fa: "calendar-days" },
    { name: "Data Entry", fa: "keyboard" },
    { name: "Web Research", fa: "magnifying-glass" },
    { name: "Documents", fa: "file-lines" },
    { name: "Email Support", fa: "envelope" },
    { name: "File Organization", fa: "folder-tree" },
    { name: "Customer Support", fa: "headset" },
  ] },
];
</script>
<style scoped>
.skill-icon { width:3.5rem; height:3.5rem; margin:auto; padding:.35rem; object-fit:contain; border-radius:.65rem; }
.skill-icon--service { display:grid; place-items:center; background:rgba(37,99,235,.12); color:#2563eb; font-size:1.65rem; }
</style>
