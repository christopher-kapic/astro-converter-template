<script>
  import { onMount, onDestroy } from "svelte";
  let isMobile = false;

  onMount(() => {
    isMobile = window.innerWidth < 640;
    window.addEventListener("resize", onResize);
  });

  onDestroy(() => {
    window.removeEventListener("resize", onResize);
  });

  function onResize() {
    isMobile = window.innerWidth < 640;
  }

  let isOpen = false;

  function toggleMenu() {
    isOpen = !isOpen;
  }
</script>

<nav class="bg-purple-900 text-gray-100">
  <div class="w-full max-w-screen-xl flex items-center justify-between p-4">
    <h1 class="text-lg">
      <a href="#">#NAME#</a>
    </h1>
    {#if !isMobile}
      <ul class="flex gap-4">
        <li>
          <a
            href="/"
            class="transition hover:text-yellow-300">Home</a
          >
        </li>
        <li>
          <a
            href="/about"
            class="transition hover:text-yellow-300">About</a
          >
        </li>
        <li>
          <a
            href="/story"
            class="transition hover:text-yellow-300">Story</a
          >
        </li>
        <li>
          <a
            href="/blog"
            class="transition hover:text-yellow-300">Blog</a
          >
        </li>
        <li>
          <a
            href="/pricing"
            class="transition hover:text-yellow-300">Pricing</a
          >
        </li>
      </ul>
      <button
        class="ml-4 py-2 px-4 bg-yellow-300 rounded-full transition hover:bg-yellow-400"
      >
        Get Started
      </button>
    {:else}
      <button
        class="p-3"
        on:click={toggleMenu}
      >
        <svg
          class="h-6 w-6"
          fill="currentColor"
          viewBox="0 0 20 20"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-10H9a1 1 0 100 2h2a1 1 0 100-2zm0-3H9a1 1 0 000 2h2a1 1 0 100-2zm0 6H9a1 1 0 100 2h2a1 1 0 100-2z"
            clip-rule="evenodd"
          />
        </svg>
      </button>
    {/if}
  </div>
  {#if isOpen}
    <div class="flex flex-col gap-4 p-4">
      <a
        href="/"
        class="transition hover:text-yellow-300">Home</a
      >
      <a
        href="/about"
        class="transition hover:text-yellow-300">About</a
      >
      <a
        href="/story"
        class="transition hover:text-yellow-300">Story</a
      >
      <a
        href="/blog"
        class="transition hover:text-yellow-300">Blog</a
      >
      <a
        href="/pricing"
        class="transition hover:text-yellow-300">Pricing</a
      >
      <button
        class="py-2 px-4 bg-yellow-300 rounded-full transition hover:bg-yellow-400"
      >
        Get Started
      </button>
    </div>
  {/if}
</nav>

<style>
  @media (max-width: 639px) {
    nav ul {
      display: none;
      position: absolute;
      top: 60px;
      right: 0;
      width: 100%;
      background-color: rgb(97, 65, 104);
      border-radius: 0.25rem;
      padding: 0.5rem;
    }

    nav ul li {
      margin-bottom: 0.5rem;
    }

    nav ul a {
      display: block;
      padding: 0.5rem;
    }

    nav ul button {
      display: block;
      margin-top: 0.5rem;
      margin-left: auto;
      margin-right: auto;
    }

    nav .hamburger {
      display: block;
    }
  }
</style>
