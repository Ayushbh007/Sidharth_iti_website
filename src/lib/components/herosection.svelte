<script lang="ts">
  import { onMount } from 'svelte';

  export let images: string[] = [
    '/images/slide_2.jpg',
    '/images/slide_3.jpg',
  ];

  export let announcements: string[] = [
    'Admissions Open for 2026',
    'Industry-Aligned Training Programs',
    'Placement Assistance Available',
    'Trusted by 5,000+ Students'
  ];

  let currentIndex = 0;
  let intervalId: number;
  let touchStartX = 0;
  let touchEndX = 0;
  const swipeThreshold = 50;

  function changeSlide(direction: number) {
    currentIndex = (currentIndex + direction + images.length) % images.length;
    resetTimer();
  }

  function handleTouchStart(e: TouchEvent) {
    touchStartX = e.changedTouches[0].screenX;
  }

  function handleTouchEnd(e: TouchEvent) {
    touchEndX = e.changedTouches[0].screenX;
    handleSwipe();
  }

  function handleSwipe() {
    const diff = touchStartX - touchEndX;
    if (Math.abs(diff) > swipeThreshold) {
      if (diff > 0) {
        changeSlide(1); // Swipe left, go to next
      } else {
        changeSlide(-1); // Swipe right, go to previous
      }
    }
  }

  function resetTimer() {
    clearInterval(intervalId);
    intervalId = window.setInterval(() => {
      currentIndex = (currentIndex + 1) % images.length;
    }, 5000);
  }

  onMount(() => {
    resetTimer();
    return () => clearInterval(intervalId);
  });
</script>

<!-- HERO SLIDESHOW -->
<section
  class="relative h-[80vh] w-full overflow-hidden cursor-grab active:cursor-grabbing"
  on:touchstart={handleTouchStart}
  on:touchend={handleTouchEnd}
>
  <div class="absolute inset-0">
    {#each images as img, i}
      <img
        src={img}
        alt=""
        class="absolute inset-0 h-full w-full object-cover transition-opacity duration-1000"
        class:opacity-100={i === currentIndex}
        class:opacity-0={i !== currentIndex}
      />
    {/each}
    <div class="absolute inset-0 bg-black/40"></div>
  </div>

  <!-- Left Button -->
  <button
    on:click={() => changeSlide(-1)}
    class="absolute left-4 top-1/2 z-10 -translate-y-1/2 transform rounded-full bg-white/20 p-3 text-white transition-all hover:bg-white/40 focus:outline-none"
    aria-label="Previous slide"
  >
    <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
    </svg>
  </button>

  <!-- Right Button -->
  <button
    on:click={() => changeSlide(1)}
    class="absolute right-4 top-1/2 z-10 -translate-y-1/2 transform rounded-full bg-white/20 p-3 text-white transition-all hover:bg-white/40 focus:outline-none"
    aria-label="Next slide"
  >
    <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
    </svg>
  </button>
</section>

<!-- CONTINUOUS ANNOUNCEMENT BAR -->
<section class="w-full overflow-hidden bg-gray-900">
  <div class="relative flex h-12 items-center">
    <div class="marquee flex min-w-full shrink-0 items-center gap-12 px-6 text-sm font-medium text-gray-100">
      {#each announcements as item}
        <span>{item}</span>
      {/each}
    </div>

    <div
      class="marquee flex min-w-full shrink-0 items-center gap-12 px-6 text-sm font-medium text-gray-100"
      aria-hidden="true"
    >
      {#each announcements as item}
        <span>{item}</span>
      {/each}
    </div>
  </div>
</section>

<style>
  @keyframes marquee {
    from {
      transform: translateX(0%);
    }
    to {
      transform: translateX(-100%);
    }
  }

  .marquee {
    animation: marquee 30s linear infinite;
  }
</style>
