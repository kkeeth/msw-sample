<template>
  <div>Hello, MSW!!</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "App",
  setup() {
    if (process.env.NODE_ENV === 'development') {
      import('./mocks/browser').then(module => {
        module.worker.start()
      })
    }
  },
});
</script>
