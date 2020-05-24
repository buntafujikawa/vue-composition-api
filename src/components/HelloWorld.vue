<template>
  <button @click="increment">
    Count is: {{ state.count }}, double is: {{ state.double }}
  </button>
</template>

<script>
  import { computed, onMounted, reactive, watchEffect } from "@vue/composition-api";

  export default {
    setup() {
      onMounted(() => {
        console.log('mounted!')
      })

      const state = reactive({
        count: 0,
        double: computed(() => state.count * 2)
      })

      function increment() {
        state.count++
      }

      watchEffect(() => console.log(state.count))

      return {
        state,
        increment
      }
    }
  }
</script>
