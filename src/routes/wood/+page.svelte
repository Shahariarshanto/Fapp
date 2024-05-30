<script>
  // Import necessary icons
  import wood from "../../assets/firewood.png";
  import sawWood from "../../assets/sawWood.png";
  import sTree from "../../assets/trees.png";
</script>

<main class="bg-gradient-to-b from-blue-400 to-indigo-500 min-h-screen">
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-3xl lg:text-4xl font-bold text-white mb-8 text-center">Explore Woodworking Tools</h1>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 md:gap-8">
      <!-- Round Wood Card -->
      <a href="/wood/round" class="bg-white rounded-lg shadow-md p-4 flex flex-col items-center justify-center">
        <img src={wood} alt="Round Wood" class="w-16 h-16 mb-2">
        <h2 class="text-lg font-semibold text-gray-800 mb-1">Round Wood</h2>
        <p class="text-sm text-gray-600">Calculate volume</p>
      </a>
      <!-- Saw Wood Card -->
      <a href="/wood/saw" class="bg-white rounded-lg shadow-md p-4 flex flex-col items-center justify-center">
        <img src={sawWood} alt="Saw Wood" class="w-16 h-16 mb-2">
        <h2 class="text-lg font-semibold text-gray-800 mb-1">Saw Wood</h2>
        <p class="text-sm text-gray-600">Calculate volume</p>
      </a>
      <!-- Standing Tree Card -->
      <a href="/wood/standing" class="bg-white rounded-lg shadow-md p-4 flex flex-col items-center justify-center">
        <img src={sTree} alt="Standing Tree" class="w-16 h-16 mb-2">
        <h2 class="text-lg font-semibold text-gray-800 mb-1">Standing Tree</h2>
        <p class="text-sm text-gray-600">Calculate volume</p>
      </a>
    </div>
  </div>
</main>
