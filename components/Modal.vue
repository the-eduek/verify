<template>
  <div v-if="displayCookieModal" class="fixed z-50 left-0 right-0 top-0 bottom-0 text-center flex items-center justify-center bg-gray-700 bg-opacity-50 p-6">
    <div class="bg-black text-white rounded-md inline-block text-sm md:text-lg p-4 shadow-md">
        <p>No results were we found for the search term entered.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      displayCookieModal: true
    }
  },

  methods: {
    closeCookieModal() {
      this.displayCookieModal =  false;
    }
  }  
}
</script>