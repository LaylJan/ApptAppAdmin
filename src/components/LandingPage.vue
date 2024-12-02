<template>
  <div class="p-8">
    <h1 class="text-2xl font-bold mb-6">Appointments</h1>
    <div class="overflow-x-auto">
      <table class="min-w-full border-collapse border border-gray-300">
        <thead>
          <tr class="bg-gray-200">
            <th class="border border-gray-300 px-4 py-2 text-left">Name</th>
            <th class="border border-gray-300 px-4 py-2 text-left">Email</th>
            <th class="border border-gray-300 px-4 py-2 text-left">Number</th>
            <th class="border border-gray-300 px-4 py-2 text-left">Doctor</th>
            <th class="border border-gray-300 px-4 py-2 text-left">Schedule</th>
            <th class="border border-gray-300 px-4 py-2 text-left">Status</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="appointment in appointments"
            :key="appointment._id"
            class="even:bg-gray-50 hover:bg-gray-100"
          >
            <td class="border border-gray-300 px-4 py-2">
              {{ appointment.name }}
            </td>
            <td class="border border-gray-300 px-4 py-2">
              {{ appointment.email }}
            </td>
            <td class="border border-gray-300 px-4 py-2">
              {{ appointment.number }}
            </td>
            <td class="border border-gray-300 px-4 py-2">
              {{ appointment.doctor }}
            </td>
            <td class="border border-gray-300 px-4 py-2">
              {{ appointment.schedule }}
            </td>
            <td class="border border-gray-300 px-4 py-2 text-center">
              <span v-if="appointment.approved === false">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                  class="inline-block hover:text-green-500"
                  @click="toggleApproval(appointment)"
                >
                  <path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M12 21a9 9 0 1 0 0-18a9 9 0 0 0 0 18m-.232-5.36l5-6l-1.536-1.28l-4.3 5.159l-2.225-2.226l-1.414 1.414l3 3l.774.774z"
                    clip-rule="evenodd"
                  />
                </svg>
              </span>
              <span v-else class="text-green-500 font-bold"> Approved </span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import axios from "axios";

export default {
  name: "LandingPage",
  setup() {
    const appointments = ref([]);

    onMounted(async () => {
      try {
        const response = await axios.get(
          "http://localhost:5000/api/appointments"
        );
        appointments.value = response.data;
      } catch (error) {
        console.error("Failed to fetch appointments:", error);
      }
    });

    const toggleApproval = async (appointment) => {
      try {
        // Update approval in the backend
        await axios.put(`http://localhost:5000/api/appointments/${appointment._id}`, {
          approved: true, // Set to true when clicked
        });

        // Update approval in the local list
        appointment.approved = true;
      } catch (error) {
        console.error('Failed to update approval status:', error);
      }
    };

    return { appointments, toggleApproval };
  },
};
</script>
