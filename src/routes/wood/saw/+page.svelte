<script>
  // Declare variables for length, width, height, and volumes
  let lengthInches = 0;
  let widthInches = 0;
  let heightInches = 0;
  let volumeCubicFeet = 0;
  let volumeCubicMeter = 0;

  // Function to calculate volume based on input values
  function calculateVolume() {
    // Convert inches to feet
    const lengthFeet = lengthInches / 12;
    const widthFeet = widthInches / 12;
    const heightFeet = heightInches / 12;

    // Calculate volume in cubic feet
    volumeCubicFeet = lengthFeet * widthFeet * heightFeet;

    // Convert cubic feet to cubic meters
    volumeCubicMeter = volumeCubicFeet * 0.0283168;
  }

  // Function to reset input values and calculated volumes
  function clearValues() {
    lengthInches = 0;
    widthInches = 0;
    heightInches = 0;
    volumeCubicFeet = 0;
    volumeCubicMeter = 0;
  }
</script>

<main class="flex flex-col items-center justify-center min-h-screen bg-gradient-to-r from-yellow-400 to-orange-500 p-4">
  <div class="w-full max-w-lg bg-white rounded-lg shadow-md p-6">
    <h1 class="text-3xl font-bold mb-6 text-center text-gray-700">Saw Wood Volume Calculator</h1>
    <div class="space-y-4">
      <!-- Input for length in inches -->
      <label class="block">
        <span class="text-gray-700">Length in Inches</span>
        <input
          type="number"
          bind:value={lengthInches}
          placeholder="Enter length in inches"
          class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
        />
      </label>
      <!-- Input for width in inches -->
      <label class="block">
        <span class="text-gray-700">Width in Inches</span>
        <input
          type="number"
          bind:value={widthInches}
          placeholder="Enter width in inches"
          class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
        />
      </label>
      <!-- Input for height in inches -->
      <label class="block">
        <span class="text-gray-700">Height in Inches</span>
        <input
          type="number"
          bind:value={heightInches}
          placeholder="Enter height in inches"
          class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
        />
      </label>
      <!-- Buttons for calculation and clearing -->
      <div class="flex justify-between">
        <button on:click={calculateVolume} class="py-2 px-4 bg-green-600 text-white font-semibold rounded-md shadow hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2">Calculate</button>
        <button on:click={clearValues} class="py-2 px-4 bg-red-600 text-white font-semibold rounded-md shadow hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2">Clear</button>
      </div>
    </div>
    <!-- Display volume in cubic feet -->
    <div class="mt-6 p-4 bg-gray-50 rounded-lg shadow-inner text-center">
      <p class="text-lg font-medium">Volume in Cubic Feet: <span class="text-green-600">{volumeCubicFeet.toFixed(2)}</span> ft³</p>
    </div>
    <!-- Display volume in cubic meters -->
    <div class="mt-4 p-4 bg-gray-50 rounded-lg shadow-inner text-center">
      <p class="text-lg font-medium">Volume in Cubic Meters: <span class="text-green-600">{volumeCubicMeter.toFixed(2)}</span> m³</p>
    </div>
  </div>
</main>
