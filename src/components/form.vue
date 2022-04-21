<template>
  <div class="flex flex-col">
    <LicensePlateInput
      v-model="licensePlate"
      @update:licensePlate="verifyVehicle"
      type="text"
      class="m-5"
    />

    <div class="flex justify-end mt-6">
      <button
        @click:license_Plate="verifyVehicle"
        type="button"
        class="font-mono py-2 px-4 m-5 bg-black hover:bg-gray-700 focus:ring-gray-500 focus:ring-offset-gray-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2 rounded-lg"
      >
        Verify
      </button>
    </div>
    <!-- alert components -->
    <component :is="verifyVehicle" />
    <!-- -->
  </div>
</template>

<script setup>
/*
  imports
 */
import { ref, reactive } from "@vue/reactivity";
import LicensePlateInput from "./licensePlateInput.vue";
import AccessAlert from "./accessAlert.vue";
import StolenModel from "./stolenModel.vue";
import NotFoundAlert from "./notFoundAlert.vue";
import { computed } from "@vue/runtime-core";
import emailjs from "@emailjs/browser";

/*
    license Plate
   */

const licensePlate = ref("");

/*
    email to head office
   */
const serviceID = ref("service_da7ze8v");
const templateID = ref("template_ppuhr5y");
const publicKey = ref("YuklJjwb-Qe4FSPDX");

const templateParams = reactive({
  name: "Head Office",
  email: "dellan4dev@gmail.com",
  message:
    "A vehicle that was verified at the compound was identified as stolen!!! Please take the nessasary action to deal with this.",
});

/*
    vehicle management system
   */

const vehicleManagementSystem = reactive({
  allowedVehicles: ["NP 20147", "NJ 203443", "ND 305742"],
  stolenVehicles: ["NUR 90221", "GP 203676", "ND 343231"],
});

const verifyVehicle = computed((val) => {
  val = licensePlate.value;
  console.log(val);
  if (vehicleManagementSystem.allowedVehicles.includes(val)) {
    return AccessAlert;
  } else if (vehicleManagementSystem.stolenVehicles.includes(val)) {
    emailjs
      .send(serviceID.value, templateID.value, templateParams, publicKey.value)
      .then(
        (result) => {
          console.log("SUCCESS!", result.status, result.text);
        },
        (error) => {
          console.log("FAILED...", error);
        }
      );
    return StolenModel;
  } else if (!val && val == "") {
    alert("Please enter in a vehicle License Plate");
  } else {
    return NotFoundAlert;
  }
});
</script>
