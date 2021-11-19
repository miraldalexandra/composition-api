<template>
  <div class="home">
    <p>{{ name }} is {{ age }}</p>
    <p ref="referenceIT">{{ name }}</p>
    <button @click="handleClick">click</button>
  </div>
</template>

<script>
import { ref } from "vue";
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "Home",
  components: {},
  setup() {
    console.log("setup");
    const referenceIt = ref(null);

    let name = "John";
    let age = 35;

    const handleClick = () => {
      console.log("clicked ref", referenceIt);
    };
    return {
      name,
      age,
      handleClick,
      referenceIT,
    };
  },
  // created() {
  //   console.log("created");
  // },
  // mounted() {
  //   console.log("mounted");
  // },
};
</script>
