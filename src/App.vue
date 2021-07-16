<template>
  <div>
    <ul>
      <li :key="user.id" v-for="user in state.users">
        <p>id: {{ user.id }}</p>
        <p>name: {{ user.name }}</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, onMounted } from "vue";
type User = {
  id: number;
  name: string;
}

export default defineComponent({
  name: "App",
  setup() {
    const state = reactive({
      users: [] as User[]
    })

    onMounted(async () => {
      const res = await fetch('/users')
      state.users = await res.json()
    })

    return { state }
  },
});
</script>
