<template>
  <div>
    <div class="flex">
      <div v-for="(element,index) in steps" :key="index" v-bind:class="'w-1/'+steps.length">
        <div class="relative mb-2">
          <div
            class="w-10 h-10 mx-auto bg-green-500 rounded-full text-lg text-white flex items-center"
          >
            <span class="text-center text-white w-full">
              <svg
                class="w-full fill-current"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                width="24"
                height="24"
              >
                <path
                  class="heroicon-ui"
                  d="M5 3h14a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5c0-1.1.9-2 2-2zm14 8V5H5v6h14zm0 2H5v6h14v-6zM8 9a1 1 0 1 1 0-2 1 1 0 0 1 0 2zm0 8a1 1 0 1 1 0-2 1 1 0 0 1 0 2z"
                />
              </svg>
            </span>
          </div>
          <div
            class="absolute flex align-center items-center align-middle content-center"
            style="width: calc(100% - 2.5rem - 1rem); top: 50%; transform: translate(-50%, -50%)"
          >
            <div v-if="index > 0" class="w-full bg-gray-200 rounded items-center align-middle align-center flex-1">
              <div  :style="currentStep+1 > index ? 'width :100%;' : 'width :0%;'" class="w-0 bg-green-300 py-1 rounded" ></div>
            </div>
          </div>
        </div>

        <div class="text-xs text-center md:text-base">{{element.title}}</div>
      </div>
    </div>

    <div v-for="(element,index) in steps" :key="index">
      <div v-if="index == currentStep ">
        <div class="flex justify-center mt-4">
          <h3 class="text-4xl font-bold">{{element.question}}</h3>
        </div>
        <div v-on:click="currentStep++" class="flex my-4 pa-1 flex-wrap justify-center">
          <g-link
            v-for="(element,index) in element.choices"
            :key="index"
            v-bind:class="'text-3xl text-center bg-transparent hover:text-blue-700 font-semibold mx-4 my-2 px-4 py-4 border-2 hover:border-blue-500 border-gray-600 text-gray-700 rounded-full'"
          >{{element}}</g-link>
        </div>
      </div>
    </div>

      <div v-if="currentStep > steps.length-1" class="flex justify-center mt-4">
         <h1 class="text-5xl font-bold"> Result! </h1>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentStep: 0
    };
  },
  props: {
    steps: {
      type: Array,
      default: () => [
        {
          title: "Hey 1",
          question: "Question 1?",
          choices: ["answer 11", "answer 12"],
        },
        {
          title: "Hey 2",
          question: "Question 2 ?",
          choices: ["answer 21", "answer 22", "answer 23"],
        },
        {
          title: "Hey 3",
          question: "Question 3 ?",
          choices: ["answer 31", "answer 32", "answer 33", "answer 34"],
        },
      ],
    },
  },
  methods: {},
};
</script>