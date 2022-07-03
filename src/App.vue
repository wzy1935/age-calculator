<template>
  <div class=" bg-gray-200 min-h-screen">
    <div class=" text-2xl font-bold text-center pt-8">{{strict ? accuracy : 100}}% Accurate Age Calculator</div>
    <div class="flex justify-center mt-8">
      <div class=" max-w-2xl w-full bg-white rounded-lg p-8">

        <p class=" m-2">Please input your age:</p>
        <input v-model="age" @blur="calAcc" type="number" min="0" class=" p-2 m-2 bg-gray-50 rounded-sm w-full outline-none"/>

        <div v-if="advanced">
          <p class=" m-2">Please input accuracy:</p>
          <input v-model="accuracy" @blur="calAcc" type="number" min="0" max="100" class=" p-2 m-2 bg-gray-50 rounded-sm w-full outline-none"/>

          <p class=" m-2">Strict Mode:</p>
          <div class=" rounded-sm overflow-hidden w-32 m-2">
            <button class=" w-16 p-1" @click="strict = true" :class=" strict ? ' bg-blue-500 hover:bg-blue-400 active:bg-blue-500 text-white' : ' bg-gray-50 hover:bg-gray-100 active:bg-gray-200'">ON</button>
            <button class=" w-16 p-1" @click="strict = false" :class=" !strict ? ' bg-blue-500 hover:bg-blue-400 active:bg-blue-500 text-white' : ' bg-gray-50 hover:bg-gray-100 active:bg-gray-200'">OFF</button>
          </div>
        </div>

        <hr class=" mt-4 mb-2 mx-2"/>

        <div>
          <button @click="cal" class=" bg-blue-500 hover:bg-blue-400 active:bg-blue-500 text-white px-2 py-1 rounded-sm m-2">Calculate</button>
          <button @click="advanced = !advanced" class=" bg-blue-500 hover:bg-blue-400 active:bg-blue-500 text-white px-2 py-1 rounded-sm m-2">{{advanced ? 'Hide' : 'Show'}} Advanced Options</button>
        </div>

        <div v-if="caled">
          <p class=" mx-2">Your age is: <span class="font-bold">{{actual}}</span></p>
        </div>
      </div>
    </div>
  </div>
</template>



<script>
export default {

  data() {
    return {
      age: 18,
      actual: 19,
      accuracy: 90,
      strict: false,
      advanced: false,
      caled: false
    }
  },

  methods: {
    calAcc() {
      this.accuracy = Math.min(100, Math.max(0, Number(this.accuracy)))
      this.age = Math.max(0, Number(this.age))
    },
    cal() {
      this.actual = Number.parseInt(this.age * this.accuracy / 100)
      this.caled = true
    }
  }

}
</script>
