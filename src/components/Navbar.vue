<template>
    <div class="bg-yellow-500 text-white shadow-lg">
      <div class="container mx-auto px-4 py-3 flex justify-between items-center">
        <!-- Logo -->
        <div class="flex items-center space-x-3">
          <img src="../assets/logo.png" alt="Logo" class="w-12 h-12" />
        </div>
  
        <!-- Navigation Links -->
        <div class="flex space-x-8">
          <a href="#" class="hover:text-blue-600 transition">Appointments</a>
          <a href="#" class="hover:text-blue-600 transition">Schedules</a>
          <a href="#" class="hover:text-blue-600 transition">Doctors</a>
          <a href="#" class="hover:text-blue-600 transition">History</a>
        </div>
  
      </div>
    </div>
  </template>
  
  <script>

  
  export default {
    name: "NavbarComponent",
    components: {

    },
    data() {
      return {
        showScheduleModal: false,
        doctors: [
  
        ],
      };
    },
  };
  </script>
  