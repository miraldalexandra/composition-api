<template>
  <div>
    <h2>computed</h2>
    <input type="text" v-model="search" />
    <p>search term: {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      <p>{{ name }}</p>
    </div>
    <button @click="handleClick">stop wtching</button>
  </div>
</template>

<script>
import { ref, computed, watch, watchEffect } from "vue";

export default {
  name: "Computed",
  setup() {
    const search = ref("");
    const names = ref(["John", "Jack", "Max", "Alina", "Lina"]);
    // const name = computed(() => {
    //   return "john";
    // });

    const stopWatch = watch(search, () => {
      console.log("watch func run");
    });

    // don't need to watch the watch-list
    const stopWatchEffect = watchEffect(() => {
      console.log("watch effect func run", search.value);
    });

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value));
    });

    const handleClick = () => {
      stopWatch();
      stopWatchEffect();
    };

    return {
      names,
      search,
      matchingNames,
      handleClick,
    };
  },
};
</script>

<style>
</style>