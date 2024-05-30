<script>
  // Declare variables for diameter and height of the standing tree
  let diameterInches = 0;
  let heightFeet = 0;
  let volumeCubicFeet = 0;
  let volumeCubicMeter = 0;

  // Function to calculate volume based on input values
  function calculateVolume() {
    // Calculate volume in cubic feet using the formula for a cone
    volumeCubicFeet = Math.PI * (diameterInches / 24) ** 2 * heightFeet / 3;

    // Convert cubic feet to cubic meters
    volumeCubicMeter = volumeCubicFeet * 0.0283168;
  }

  // Function to reset input values and calculated volumes
  function clearValues() {
    diameterInches = 0;
    heightFeet = 0;
    volumeCubicFeet = 0;
    volumeCubicMeter = 0;
  }
</script>

<main class="flex flex-col items-center justify-center min-h-screen bg-gradient-to-r from-purple-400 to-indigo-600 p-4">
  <div class="w-full max-w-lg bg-white rounded-lg shadow-md p-6">
    <h1 class="text-3xl font-bold mb-6 text-center text-gray-700">Standing Tree Volume Calculator</h1>
    <div class="space-y-4">
      <!-- Input for diameter in inches -->
      <label class="block">
        <span class="text-gray-700">Diameter at Breast Height (DBH) in Inches</span>
        <input
          type="number"
          bind:value={diameterInches}
          placeholder="Enter diameter in inches"
          class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
        />
      </label>
      <!-- Input for height in feet -->
      <label class="block">
        <span class="text-gray-700">Height in Feet</span>
        <input
          type="number"
          bind:value={heightFeet}
          placeholder="Enter height in feet"
          class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
        />
      </label>
      <!-- Buttons for calculation and clearing -->
      <div class="flex justify-between">
        <button on:click={calculateVolume} class="py-2 px-4 bg-purple-600 text-white font-semibold rounded-md shadow hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2">Calculate</button>
        <button on:click={clearValues} class="py-2 px-4 bg-red-600 text-white font-semibold rounded-md shadow hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2">Clear</button>
      </div>
    </div>
    <!-- Display volume in cubic feet -->
    <div class="mt-6 p-4 bg-gray-50 rounded-lg shadow-inner text-center">
      <p class="text-lg font-medium">Volume in Cubic Feet: <span class="text-purple-600">{volumeCubicFeet.toFixed(2)}</span> ft³</p>
    </div>
    <!-- Display volume in cubic meters -->
    <div class="mt-4 p-4 bg-gray-50 rounded-lg shadow-inner text-center">
      <p class="text-lg font-medium">Volume in Cubic Meters: <span class="text-purple-600">{volumeCubicMeter.toFixed(2)}</span> m³</p>
    </div>
  </div>
</main>
