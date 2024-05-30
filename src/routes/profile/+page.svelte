<script>
  let editMode = false;
  
  let user = {
    name: "John Doe",
    email: "john@example.com",
    phone: "123-456-7890",
    age: 30,
    country: "United States",
    job: "Software Engineer",
    // Add more essential information as needed
  };

  // Function to toggle edit mode
  function toggleEditMode() {
    editMode = !editMode;
  }

  // Function to update user information
  function updateProfile() {
    // Update user information (this could involve making an API request)
    console.log("User information updated successfully!");
    // After updating, switch back to view mode
    toggleEditMode();
  }
</script>

<main class="bg-gradient-to-b from-blue-400 to-indigo-500 min-h-screen">
  <div class="container mx-auto px-4 py-8">
    <h1 class="text-3xl lg:text-4xl font-bold text-white mb-8 text-center">User Profile</h1>
    <div class="max-w-md mx-auto bg-white rounded-lg shadow-md p-6">
      {#if !editMode}
        <!-- View mode -->
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Name</label>
          <p class="mt-1 text-sm text-gray-900">{user.name}</p>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Email</label>
          <p class="mt-1 text-sm text-gray-900">{user.email}</p>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Phone</label>
          <p class="mt-1 text-sm text-gray-900">{user.phone}</p>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Age</label>
          <p class="mt-1 text-sm text-gray-900">{user.age}</p>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Country</label>
          <p class="mt-1 text-sm text-gray-900">{user.country}</p>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Job</label>
          <p class="mt-1 text-sm text-gray-900">{user.job}</p>
        </div>
        <!-- Edit button -->
        <div class="text-center">
          <button class="px-6 py-2 bg-blue-500 text-white font-semibold rounded-md shadow-md hover:bg-blue-600 hover:text-white transition-colors" on:click={toggleEditMode}>Edit Profile</button>
        </div>
      {:else}
        <!-- Edit mode -->
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Name</label>
          <input type="text" class="w-full px-4 py-2 mt-1 rounded-md border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={user.name}>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Email</label>
          <input type="email" class="w-full px-4 py-2 mt-1 rounded-md border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={user.email}>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Phone</label>
          <input type="tel" class="w-full px-4 py-2 mt-1 rounded-md border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={user.phone}>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Age</label>
          <input type="number" class="w-full px-4 py-2 mt-1 rounded-md border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={user.age}>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Country</label>
          <input type="text" class="w-full px-4 py-2 mt-1 rounded-md border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={user.country}>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Job</label>
          <input type="text" class="w-full px-4 py-2 mt-1 rounded-md border border-gray-300 focus:outline-none focus:border-blue-500" bind:value={user.job}>
        </div>
        <!-- Save button -->
        <div class="text-center">
          <button class="px-6 py-2 bg-blue-500 text-white font-semibold rounded-md shadow-md hover:bg-blue-600 hover:text-white transition-colors" on:click={updateProfile}>Save</button>
        </div>
      {/if}
    </div>
  </div>
</main>
