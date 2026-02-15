<script setup>
import { reactive, ref } from "vue";

let inputs = [
  {
    label: "Your name",
    key: "name",
    placeholder: "Enter your name",
    type: "text",
  },
  {
    label: "Your surname",
    key: "surname",
    placeholder: "Enter your surname",
    type: "text",
  },
  {
    label: "Phone number",
    key: "phone",
    placeholder: "Enter your phone number",
    type: "tel",
  },
];

let teachers = ["Amour Teacher", "Muhsina Teacher", "Yusufxon Teacher"];

const formData = reactive({
  name: "",
  surname: "",
  phone: "",
  teacher: "",
});

let error_style = ref(false);

const submitForm = () => {
  if (formData["name"] == "") {
    error_style.value = true;
    setTimeout(() => {
      error_style.value = false;
    }, 1500);
  } else if (formData["surname"] == "") {
    error_style.value = true;
    setTimeout(() => {
      error_style.value = false;
    }, 1500);
  } else if (formData["phone"] == "") {
    error_style.value = true;
    setTimeout(() => {
      error_style.value = false;
    }, 1500);
  } else if (formData["teacher"] == "") {
    error_style.value = true;
    setTimeout(() => {
      error_style.value = false;
    }, 1500);
  } else {
    console.log(formData);
  }
};
</script>

<template>
  <div class="flex justify-center items-center min-h-screen">
    <div class="book flex justify-center">
      <div class="flex flex-col gap-5 ml-5">
        <ul v-for="(input, index) in inputs" :key="index" class="space-y-2">
          <li>{{ input.label }}</li>
          <input
            :type="input.type"
            :placeholder="input.placeholder"
            v-model="formData[input.key]"
            :class="[
              'border border-[#e8e8e8] p-2 rounded-2xl bg-[#e8e8e8] shadow-[20px_20px_60px_#c5c5c5,-20px_-20px_60px_#ffffff] transition-all duration-300 focus:outline-[#e8e8e8] focus:bg-[#e8e8e8] focus:shadow-[inset_20px_20px_60px_#c5c5c5,inset_-20px_-20px_60px_#ffffff]',
              error_style ? 'border border-red-500' : '',
            ]"
          />
        </ul>
        <select
          v-model="formData.teacher"
          :class="[
            `appearance-none bg-[#e8e8e8] border border-[#e8e8e8] outline-none rounded-2xl py-2 px-4 cursor-pointer`,
            error_style ? 'border border-red-500' : '',
          ]"
        >
          <option value="" disabled>Choose your teacher</option>

          <option
            v-for="(teacher, index) in teachers"
            :key="index"
            :value="teacher"
          >
            {{ teacher }}
          </option>
        </select>

        <button
          class="flex justify-center items-center mx-auto shadow-xl text-lg bg-gray-50 backdrop-blur-md lg:font-semibold cursor-pointer px-6 py-1 border rounded-full group"
          @click="submitForm"
        >
          Register
        </button>
      </div>
      <div class="cover">
        <p>Excellence School</p>
        <p>Register</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.book {
  position: relative;
  border-radius: 10px;
  width: 300px;
  height: 420px;
  background-color: whitesmoke;
  -webkit-box-shadow: 1px 1px 12px #000;
  box-shadow: 1px 1px 12px #000;
  -webkit-transform: preserve-3d;
  -ms-transform: preserve-3d;
  transform: preserve-3d;
  -webkit-perspective: 2000px;
  perspective: 2000px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  color: #000;
}

.cover {
  top: 0;
  position: absolute;
  background-color: lightgray;
  width: 100%;
  height: 100%;
  border-radius: 10px;
  cursor: pointer;
  -webkit-transition: all 0.5s;
  transition: all 0.5s;
  -webkit-transform-origin: 0;
  -ms-transform-origin: 0;
  transform-origin: 0;
  -webkit-box-shadow: 1px 1px 12px #000;
  box-shadow: 1px 1px 12px #000;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}

.book:hover .cover {
  -webkit-transition: all 0.5s;
  transition: all 0.5s;
  -webkit-transform: rotatey(-80deg);
  -ms-transform: rotatey(-80deg);
  transform: rotatey(-80deg);
}

p {
  font-size: 20px;
  font-weight: bolder;
}
</style>