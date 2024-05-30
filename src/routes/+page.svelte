<script>
  // Import necessary icons
  import wood from "../assets/wood.png";
  import age from "../assets/age.png";
</script>

<main class="bg-gradient-to-b from-blue-400 to-indigo-500 min-h-screen">
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-4xl font-bold text-white mb-8 text-center">Welcome to Your App</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <!-- Wood Calculator Card -->
      <a href="/wood" class="bg-white rounded-lg shadow-md p-6 flex flex-col items-center justify-center">
        <img src={wood} alt="Wood Calculator" class="w-16 h-16 mb-4">
        <h2 class="text-lg font-semibold text-gray-800 mb-2">Wood Calculator</h2>
        <p class="text-sm text-gray-600">Calculate wood volume</p>
      </a>
      <!-- Age Calculator Card -->
      <a href="/age" class="bg-white rounded-lg shadow-md p-6 flex flex-col items-center justify-center">
        <img src={age} alt="Age Calculator" class="w-16 h-16 mb-4">
        <h2 class="text-lg font-semibold text-gray-800 mb-2">Age Calculator</h2>
        <p class="text-sm text-gray-600">Calculate age</p>
      </a>
      <!-- ScientificNames Card -->
      <a href="/ScientificNames" class="bg-white rounded-lg shadow-md p-6 flex flex-col items-center justify-center">
        <img src={age} alt="Scientific Names" class="w-16 h-16 mb-4">
        <h2 class="text-lg font-semibold text-gray-800 mb-2">Scientific Names</h2>
        <p class="text-sm text-gray-600">Scientific Names</p>
      </a>
    </div>
  </div>
</main>
