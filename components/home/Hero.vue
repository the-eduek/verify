<template>
  <section class="container px-4 py-28 mx-auto">
    <div class="w-full mx-auto text-center md:w-11/12 xl:w-8/12">
      <h1 class="mb-3 text-4xl font-bold text-gray-900 md:text-5xl md:leading-tight md:font-extrabold">Power your finance, grow your business.</h1>
      <p class="mb-6 text-lg text-gray-700 md:text-xl md:leading-normal font-light py-5">Empower your business with all the right tools to accept online payments and provide the best customer experience.</p>
      <form  class="relative w-full max-w-xl mx-auto" @submit.prevent="submitSearch">
        <input ref="searchBar" v-model="search" type="search" class="w-full pl-4 py-2 pr-9 border border-gray-400 rounded-md focus:outline-none focus:ring focus:ring-gray-300" placeholder="Search for individuals, professionals or organizations." />
        <svg fill="currentColor" width="24" height="24" viewBox="0 0 24 24" class="absolute right-2 top-2.5 text-sm cursor-pointer" @click="submitSearch"><path d="M9.5,3A6.5,6.5 0 0,1 16,9.5C16,11.11 15.41,12.59 14.44,13.73L14.71,14H15.5L20.5,19L19,20.5L14,15.5V14.71L13.73,14.44C12.59,15.41 11.11,16 9.5,16A6.5,6.5 0 0,1 3,9.5A6.5,6.5 0 0,1 9.5,3M9.5,5C7,5 5,7 5,9.5C5,12 7,14 9.5,14C12,14 14,12 14,9.5C14,7 12,5 9.5,5Z"></path></svg>
      </form>
      <div>
        <div v-for="data in searchResults" :key="data.id" class="max-w-xl mx-auto">
          <div class="border border-gray-400 rounded-md p-4 my-4 bg-white font-light text-left">
            <div class="flex items-center">
              <h1 class="text-xl">{{ data.name }}</h1>            
              <div class="w-4 h-4 ml-2">
                <img src="~/assets/images/verify.png" alt="verify icon" class="max-w-full">
              </div>
            </div>
            <small class="font-semibold">{{ data.occupation }}, {{ data.company.name }}.</small>
            <div class="font-light border-t border-gray-400 mt-5">
              <p class="pt-5">📞 +{{ data.phone }}</p>
              <p>📧 {{ data.email.toLowerCase() }}</p>
              <p>🔗 <a :href="'https://'+ data.website" class="underline">https://{{ data.website }}</a></p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-if="displayResultsModal" class="fixed z-50 left-0 right-0 top-0 bottom-0 text-center flex items-center justify-center bg-gray-700 bg-opacity-50 p-6" @click=closeResultsModal>
      <p class="bg-black text-white rounded-md inline-block text-sm md:text-lg px-6 py-4 shadow-md">No results were we found for the search term entered.</p>
    </div>
  </section>
</template>


<script>
export default {
  data() {
    return {
      dataset: [],
      search: "",
      searchResults: [],
      displayResultsModal: false,
      firstTime: true
    }
  },
  
  methods: {
    submitSearch() {
      this.searchResults = [];

      const dataResults = this.dataset.filter(data => data.name.toLowerCase().includes(this.search.toLowerCase()))
      dataResults.forEach(result => { if (this.searchResults.indexOf(result) === -1) this.searchResults.push(result) })

      const occupationResults = this.dataset.filter(data => data.occupation.toLowerCase().includes(this.search.toLowerCase()))
      occupationResults.forEach(result => { if (this.searchResults.indexOf(result) === -1) this.searchResults.push(result) })

      const companyResults = this.dataset.filter(data => data.company.name.toLowerCase().includes(this.search.toLowerCase()))
      companyResults.forEach(result => { if (this.searchResults.indexOf(result) === -1) this.searchResults.push(result) })

      if (!this.searchResults.length) this.displayResultsModal = !this.displayResultsModal      
    },

    closeResultsModal() {
      this.displayResultsModal = !this.displayResultsModal;
    }
  },
  
  async fetch() {
    this.dataset = await this.$axios.$get('http://localhost:3000/dataset');
  }
}
</script>