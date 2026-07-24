<template>
  <header class="flex justify-between items-center">
    <div class="font-semibold dark:text-cyan-400 theme-color">
      <a href="https://linkedin.com/in/rafael-cawicaan-97b9b11a2" target="_blank" rel="noreferrer">
        &#64;R.A.C
      </a>
    </div>

    <button
      ref="themeButton"
      class="theme-toggle"
      type="button"
      :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
      :aria-pressed="isDark"
      :title="isDark ? 'Light mode' : 'Dark mode'"
      @click="toggleTheme"
    >
      <span class="theme-toggle__track" aria-hidden="true">
        <span class="theme-toggle__thumb">
          <svg v-if="isDark" viewBox="0 0 24 24">
            <path d="M20.2 15.1A8.5 8.5 0 0 1 8.9 3.8 8.5 8.5 0 1 0 20.2 15.1Z" />
          </svg>
          <svg v-else viewBox="0 0 24 24">
            <circle cx="12" cy="12" r="4" />
            <path d="M12 2v2m0 16v2M4.9 4.9l1.4 1.4m11.4 11.4 1.4 1.4M2 12h2m16 0h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4" />
          </svg>
        </span>
      </span>
    </button>
  </header>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import { useDark, useToggle } from "@vueuse/core";

type ViewTransitionDocument = Document & {
  startViewTransition?: (update: () => void) => { ready: Promise<void> };
};

const isDark = useDark();
const toggleDark = useToggle(isDark);
const themeButton = ref<HTMLButtonElement | null>(null);

const toggleTheme = async () => {
  const reduceMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
  const startViewTransition = (document as ViewTransitionDocument).startViewTransition;

  if (!startViewTransition || reduceMotion || !themeButton.value) {
    toggleDark();
    return;
  }

  const rect = themeButton.value.getBoundingClientRect();
  const x = rect.left + rect.width / 2;
  const y = rect.top + rect.height / 2;
  const radius = Math.hypot(
    Math.max(x, window.innerWidth - x),
    Math.max(y, window.innerHeight - y)
  );
  const transition = startViewTransition.call(document, () => toggleDark());

  await transition.ready;

  document.documentElement.animate(
    { clipPath: [`circle(0px at ${x}px ${y}px)`, `circle(${radius}px at ${x}px ${y}px)`] },
    {
      duration: 850,
      easing: "cubic-bezier(0.76, 0, 0.24, 1)",
      pseudoElement: "::view-transition-new(root)",
    }
  );
};
</script>

<style lang="scss" scoped>
.theme-color {
  transition: color 600ms cubic-bezier(0.22, 1, 0.36, 1);
}

.theme-toggle {
  padding: 3px;
  border-radius: 999px;
  outline: none;
  -webkit-tap-highlight-color: transparent;

  &:focus-visible {
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.3);
  }
}

.theme-toggle__track {
  display: block;
  width: 52px;
  height: 28px;
  padding: 3px;
  border: 1px solid rgba(15, 23, 42, 0.12);
  border-radius: 999px;
  background: #e9eef5;
  box-shadow: inset 0 1px 3px rgba(15, 23, 42, 0.12);
  transition: background 500ms cubic-bezier(0.22, 1, 0.36, 1),
    border-color 500ms ease;
}

.theme-toggle__thumb {
  display: grid;
  width: 20px;
  height: 20px;
  place-items: center;
  border-radius: 50%;
  color: #9a6700;
  background: #ffd166;
  box-shadow: 0 2px 7px rgba(15, 23, 42, 0.25);
  transform: translateX(0) rotate(0deg);
  transition: transform 650ms cubic-bezier(0.34, 1.56, 0.64, 1),
    color 450ms ease, background 450ms ease;

  svg {
    width: 14px;
    height: 14px;
    fill: none;
    stroke: currentColor;
    stroke-width: 1.8;
    stroke-linecap: round;
    stroke-linejoin: round;
  }
}

:global(.dark) .theme-toggle__track {
  border-color: rgba(255, 255, 255, 0.12);
  background: #151b2b;
}

:global(.dark) .theme-toggle__thumb {
  color: #dbeafe;
  background: #334155;
  transform: translateX(24px) rotate(360deg);
}

@media (prefers-reduced-motion: reduce) {
  .theme-color,
  .theme-toggle__track,
  .theme-toggle__thumb {
    transition-duration: 0.01ms;
  }
}
</style>
