<template>
<header class="z-30 w-full px-2 py-4 bg-white sm:px-4">
  <div class="container flex items-center justify-between mx-auto">
    <div class="flex items-center font-bold pl-2">
      <h1 class="text-gray-800">verify</h1>
      <div class="w-4 h-4 ml-1.5">
        <img src="~/assets/images/verify.png" alt="verify icon" class="max-w-full">
      </div>
    </div>
    <div>
      <ul class="relative hidden space-x-10 md:inline-flex rtl:space-x-reverse">
        <li><a href="#" class="text-gray-800 hover:text-gray-900 font-bold">Home</a></li>
        <li><a href="#" class="text-gray-800 hover:text-gray-900">About</a></li>
        <li><a href="#" class="text-gray-800 hover:text-gray-900">Blog</a></li>
        <li><a href="#" class="text-gray-800 hover:text-gray-900">Pricing</a></li>
      </ul>
    </div>
    <div class="flex items-center space-x-2 rtl:space-x-reverse">
      <a href="#" class="hidden rounded-sm md:inline-flex px-5 py-2 border-solid border border-black">Login</a>
      <a href="#" class="rounded-sm bg-black text-white px-5 py-2 border-solid border border-black">Signup</a>
      <div class="inline-flex md:hidden">
        <button class="flex-none px-2 btn btn-white btn-sm" @click="open = true">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            aria-hidden="true"
            class="w-5 h-5"
          >
            <line x1="3" y1="12" x2="21" y2="12"></line>
            <line x1="3" y1="6" x2="21" y2="6"></line>
            <line x1="3" y1="18" x2="21" y2="18"></line>
          </svg>
          <span class="sr-only">Open Menu</span>
        </button>
      
      </div>
    </div>
  </div>
</header>
</template>

<script>
export default {
  data() {
    return {
      one: false,
      open: false,
      two: false
    };
  }
}
</script>