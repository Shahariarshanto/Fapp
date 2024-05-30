<script>
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';
  import { format, differenceInYears, differenceInMonths, differenceInWeeks, differenceInDays, differenceInHours, differenceInMinutes, differenceInSeconds, addYears, addMonths, addWeeks } from 'date-fns';

  let birthdate = '';
  let age = writable(null);
  let exactAge = writable({});
  let formattedBirthdate = writable('');
  let error = writable('');

  function calculateAge() {
    error.set('');
    age.set(null);
    exactAge.set({});
    formattedBirthdate.set('');

    if (!birthdate) {
      error.set('Please enter a valid birthdate.');
      return;
    }

    const today = new Date();
    const birthDate = new Date(birthdate);
    if (isNaN(birthDate)) {
      error.set('Invalid date format.');
      return;
    }

    const years = differenceInYears(today, birthDate);
    const months = differenceInMonths(today, addYears(birthDate, years));
    const days = differenceInDays(today, addYears(addMonths(birthDate, months), years));
    const totalMonths = years * 12 + months;
    const weeks = Math.floor(days / 7);
    const remainingDays = days % 7;
    const totalDays = differenceInDays(today, birthDate);
    const hours = differenceInHours(today, birthDate);
    const minutes = differenceInMinutes(today, birthDate);
    const seconds = differenceInSeconds(today, birthDate);

    age.set(years);
    exactAge.set({
      years,
      months,
      days,
      totalMonths,
      weeks,
      remainingDays,
      totalDays,
      hours,
      minutes,
      seconds
    });
    formattedBirthdate.set(format(birthDate, 'MMMM dd, yyyy'));
  }

  function resetForm() {
    birthdate = '';
    age.set(null);
    exactAge.set({});
    formattedBirthdate.set('');
    error.set('');
  }
</script>

<main class="flex flex-col items-center justify-center min-h-screen bg-gradient-to-r from-blue-400 to-purple-600 p-4">
  <div class="w-full max-w-sm bg-white rounded-lg shadow-md p-6">
    <h1 class="text-3xl font-bold mb-4 text-center text-gray-700">Age Calculator</h1>
    <form on:submit|preventDefault={calculateAge} class="space-y-4">
      <div>
        <label for="birthdate" class="block text-sm font-medium text-gray-700">Enter your birthdate:</label>
        <input
          type="date"
          id="birthdate"
          bind:value={birthdate}
          class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
          required
        />
      </div>
      <button
        type="submit"
        class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
      >
        Calculate Age
      </button>
      <button
        type="button"
        on:click={resetForm}
        class="w-full py-2 px-4 mt-2 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-red-500 hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500"
      >
        Reset
      </button>
    </form>
    {#if $error}
      <div class="mt-4 p-4 bg-red-100 border border-red-400 text-red-700 rounded-lg shadow-inner">
        <p class="text-sm">{$error}</p>
      </div>
    {/if}
    {#if $age !== null}
      <div class="mt-4 p-4 bg-gray-50 rounded-lg shadow-inner text-center">
        <p class="text-lg font-medium">Your age is: <span class="text-indigo-600">{$age} years</span></p>
        <p class="text-sm text-gray-600">Birthdate: <span class="text-gray-800">{$formattedBirthdate}</span></p>
        <div class="mt-4 text-left">
          <p class="text-md font-semibold">Exact age in different units:</p>
          <ul class="list-disc pl-5">
            <li>{$exactAge.years} years {$exactAge.months} months {$exactAge.days} days</li>
            <li>{$exactAge.totalMonths} months {$exactAge.days} days</li>
            <li>{$exactAge.weeks} weeks and {$exactAge.remainingDays} days</li>
            <li>{$exactAge.totalDays} days</li>
            <li>≈ {$exactAge.hours} hours</li>
            <li>≈ {$exactAge.minutes} minutes</li>
            <li>≈ {$exactAge.seconds} seconds</li>
          </ul>
        </div>
      </div>
    {/if}
  </div>
</main>
