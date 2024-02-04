<script setup>
import { onMounted } from "vue";
import { initFlowbite } from "flowbite";

// initialize components based on data attribute selectors
onMounted(() => {
  initFlowbite();
});
</script>

<template>
  <div id="app">
    <Weather />
  </div>

  <div
    id="custom-controls-gallery"
    class="relative w-full"
    data-carousel="slide"
  >
    <!-- Carousel wrapper -->
    <div
      class="bg-blue-100 z-0 relative h-56 overflow-hidden rounded-lg md:h-[40rem]"
    >
      <!-- Item 1 -->
      <div class="hidden duration-700 ease-in-out" data-carousel-item>
        <img
          src="https://flowbite.s3.amazonaws.com/docs/gallery/square/image-1.jpg"
          class="absolute block max-w-full h-auto -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
          alt=""
        />
      </div>
      <!-- Item 2 -->
      <div class="hidden duration-700 ease-in-out" data-carousel-item="active">
        <img
          src="https://flowbite.s3.amazonaws.com/docs/gallery/square/image-2.jpg"
          class="absolute block max-w-full h-auto -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
          alt=""
        />
      </div>
      <!-- Item 3 -->
      <div class="hidden duration-700 ease-in-out" data-carousel-item>
        <img
          src="https://flowbite.s3.amazonaws.com/docs/gallery/square/image-3.jpg"
          class="absolute block max-w-full h-auto -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
          alt=""
        />
      </div>
      <!-- Item 4 -->
      <div class="hidden duration-700 ease-in-out" data-carousel-item>
        <img
          src="https://flowbite.s3.amazonaws.com/docs/gallery/square/image-4.jpg"
          class="absolute block max-w-full h-auto -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
          alt=""
        />
      </div>
      <!-- Item 5 -->
      <div class="hidden duration-700 ease-in-out" data-carousel-item>
        <img
          src="https://flowbite.s3.amazonaws.com/docs/gallery/square/image-5.jpg"
          class="absolute block max-w-full h-auto -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
          alt=""
        />
      </div>
    </div>
    <div class="flex bg-blue-100 justify-center items-center pt-4">
      <button
        type="button"
        class="flex justify-center items-center me-4 h-full cursor-pointer group focus:outline-none"
        data-carousel-prev
      >
        <span
          class="text-gray-400 hover:text-gray-900 dark:hover:text-white group-focus:text-gray-900 dark:group-focus:text-white"
        >
          <svg
            class="rtl:rotate-180 w-5 h-5"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 14 10"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M13 5H1m0 0 4 4M1 5l4-4"
            />
          </svg>
          <span class="sr-only">Previous</span>
        </span>
      </button>
      <button
        type="button"
        class="flex justify-center items-center h-full cursor-pointer group focus:outline-none"
        data-carousel-next
      >
        <span
          class="text-gray-400 hover:text-gray-900 dark:hover:text-white group-focus:text-gray-900 dark:group-focus:text-white"
        >
          <svg
            class="rtl:rotate-180 w-5 h-5"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 14 10"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M1 5h12m0 0L9 1m4 4L9 9"
            />
          </svg>
          <span class="sr-only">Next</span>
        </span>
      </button>
    </div>
  </div>

  <section class="bg-blue-100">
    <div class="max-w-screen-xl px-4 py-8 mx-auto lg:py-16">
      <div
        class="grid items-center gap-8 mb-8 lg:mb-16 lg:gap-12 lg:grid-cols-12"
      >
        <div class="lg:col-span-6 text-center sm:mb-6 lg:text-left lg:mb-0">
          <h1
            class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl xl:text-6xl dark:text-white"
          >
            Najlepsza Villa w okolicy, lepszej nie znajdziesz
          </h1>
          <p
            class="max-w-xl mx-auto mb-6 font-light text-gray-500 lg:mx-0 xl:mb-8 md:text-lg xl:text-xl dark:text-gray-400"
          >
            Lorem ipsum dolor sit amet consectetur adipisicing elit.
            Reprehenderit voluptate praesentium, esse magnam molestiae
            recusandae architecto eius dolore eaque iusto dolores nemo
            consequuntur dignissimos! Explicabo tenetur vel molestias animi et.
          </p>
        </div>
        <!-- Komponent FacebookPage -->
        <div class="lg:col-span-5">
          <div class="flex justify-center">
            <div class="w-full lg:max-w-xl rounded-lg">
              <!-- Treść FacebookPage, załóżmy, że komponent jest odpowiednio zintegrowany -->
              <FacebookPage />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
  <footer class="p-4 bg-white md:p-8 lg:p-10 dark:bg-gray-800">
    <div class="mx-auto max-w-screen-xl text-center">
      <a
        href="#"
        class="flex justify-center items-center text-2xl space-x-10 font-semibold text-gray-900 dark:text-white"
      >
        <img src="./photos/logo.jpg" class="h-8 w-8" alt="villa" />
        VILLA
      </a>
      <p class="my-6 text-gray-500 dark:text-gray-400">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt rerum
        voluptates aperiam corporis et, quam voluptas dolor animi fuga ullam.
        Autem repellat sint assumenda architecto accusamus itaque possimus
        voluptas fuga.
      </p>
      <span class="text-sm text-gray-500 sm:text-center dark:text-gray-400"
        >© 2024 <a href="#" class="hover:underline">Dreampire</a></span
      >
    </div>
  </footer>
</template>
