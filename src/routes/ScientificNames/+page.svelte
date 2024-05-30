<script>
  let searchTerm = '';
  let searchResults = [];

  // Function to handle search
  function search() {
    // Perform search based on the searchTerm
    // For now, we'll just simulate some search results
    searchResults = [
      { commonName: 'Oak', scientificName: 'Quercus' },
      { commonName: 'Pine', scientificName: 'Pinus' },
      { commonName: 'Maple', scientificName: 'Acer' },
      // Add more search results as needed
    ];
  }
</script>

<main class="bg-gradient-to-b from-blue-400 to-indigo-500 min-h-screen">
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-3xl lg:text-4xl font-bold text-white mb-8 text-center">Search Scientific Names</h1>
    <div class="max-w-md mx-auto">
      <!-- Search input -->
      <div class="mb-4">
        <input type="text" placeholder="Enter search term" class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={searchTerm}>
      </div>
      <!-- Search button -->
      <div class="text-center">
        <button class="px-6 py-2 bg-white text-blue-500 font-semibold rounded-lg shadow-md hover:bg-blue-600 hover:text-white transition-colors" on:click={search}>Search</button>
      </div>
      <!-- Search results -->
      {#if searchResults.length > 0}
        <div class="mt-8">
          <h2 class="text-2xl font-semibold text-white mb-4">Search Results</h2>
          <ul class="space-y-4">
            {#each searchResults as result}
              <li class="bg-white rounded-lg shadow-md p-4">
                <h3 class="text-lg font-semibold text-gray-800 mb-2">{result.commonName}</h3>
                <p class="text-sm text-gray-600">{result.scientificName}</p>
              </li>
            {/each}
          </ul>
        </div>
      {:else}
        <p class="text-lg text-white text-center">No results found</p>
      {/if}
    </div>
  </div>
</main>
