<template>
  <div>
    <h1>Nuxt 2 store with Bridge demo</h1>
    <button type="button" @click="increment">
      Increment
    </button>
    <input type="number" :value="counter" disabled />
  </div>
</template>
<script>
/*import { computed, defineComponent, useStore } from '@nuxtjs/composition-api'*/
/*import { computed, useNuxtApp, defineComponent } from '#app'*/
const useStore = () => useNuxtApp().$store;

export default defineComponent({
  name: 'UseStore',
  setup() {
    const store = useStore();
    const { state, dispatch } = store;
    console.log('state.counter', state.counter);
    const counter = computed(() => state.counter);
    const increment = () => dispatch('increment');

    return { counter, increment };
  }
});
</script>
