<script lang="ts">
  import { onMount } from "svelte";

  let dropdown_visible = false;
  let location = "";
  onMount(() => {
    location = window.location.href.split("/")[3] || "";
  });
</script>

<div
  class="#nav_bg_color# #nav_text_color# w-screen h-16 sticky top-0 flex justify-center"
>
  <div
    class="items-center flex w-full max-w-screen-2xl px-2 sm:px-4 md:px-12 justify-between"
  >
    <a href="/"
      ><img alt="#business_name# Logo" class="max-h-16" src="/logo.png" /></a
    >
    <button
      class="cursor-pointer md:hidden"
      on:click={() => {
        dropdown_visible = !dropdown_visible;
      }}
    >
      {#if dropdown_visible}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      {:else}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
          />
        </svg>
      {/if}
    </button>
    <ul
      class="#nav_bg_dropdown_color# px-8 gap-8 flex flex-col items-end justify-center absolute h-screen w-screen top-16 transition-[left] {dropdown_visible
        ? 'left-0'
        : 'left-full'} md:bg-black/0 md:relative md:h-auto md:w-auto md:top-auto md:flex-row md:px-0 md:left-0 md:gap-8"
    >
      #links#
    </ul>
  </div>
</div>
