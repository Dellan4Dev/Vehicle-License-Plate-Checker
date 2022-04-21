<template>
  <div
    class="fixed top-0 left-0 w-screen h-screen z-50 bg-gray-800 bg-opacity-75 origin-center flex justify-center items-center appear-done enter-done"
  >
    <div
      class="bg-white w-11/12 max-w-md text-center pt-10 rounded-sm shadow-lg appear-done enter-done"
    >
      <div
        class="w-12 h-12 rounded-sm flex justify-center items-center bg-red-600 mb-4 mx-auto"
      >
        <svg
          class="w-6 h-6 text-white fill-current"
          viewBox="0 0 40 40"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M20 3.36667C10.8167 3.36667 3.3667 10.8167 3.3667 20C3.3667 29.1833 10.8167 36.6333 20 36.6333C29.1834 36.6333 36.6334 29.1833 36.6334 20C36.6334 10.8167 29.1834 3.36667 20 3.36667ZM19.1334 33.3333V22.9H13.3334L21.6667 6.66667V17.1H27.25L19.1334 33.3333Z"
          />
        </svg>
      </div>
      <div class="px-4 mb-4">
        <h2 class="text-3xl font-mono font-semibold text-red-500">Stolen!</h2>
        <p
          class="mt-2 w-10/12 max-w-6xl mx-auto text-gray-800 font-mono text-base"
        >
          This Vehicle Is Stolen. An E-mail has been sent to alert head office.
        </p>
      </div>
    </div>
  </div>
</template>
