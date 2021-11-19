<template>
  <div class="home">
    <h2>Home</h2>
    <h3>refs</h3>
    <p>{{ name }} is {{ age }}</p>
    <!-- <p ref="referenceIT">{{ name }}</p> -->
    <button @click="handleClick">click</button>
    <button @click="age++">add 1 to age</button>
    <input type="text" v-model="name" />
    <hr />
    <h3>refs</h3>
    <p>ninja one: {{ ninjaOne.name }} is {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">update ninja one</button>
    <hr />
    <h3>reactive</h3>
    <p>ninja two: {{ ninjaTwo.name }} is {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">update ninja two</button>
  </div>
</template>

<script>
import { ref, reactive } from "vue";
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "Home",
  setup() {
    // console.log("setup");
    // let name = "John";
    // let age = 35;
    // const referenceIt = ref(null);
    const name = ref("John");
    const age = ref(35);
    const handleClick = () => {
      // console.log("clicked ref", referenceIt);
      name.value = "Jack";
      age.value = 45;
    };

    // REF OBJECT
    const ninjaOne = ref({ name: "Max", age: 38 });
    const updateNinjaOne = () => {
      ninjaOne.value.age = 45;
    };

    // REACTIVE
    const ninjaTwo = reactive({ name: "reactive ninja", age: 55 });
    const updateNinjaTwo = () => {
      // directly access the property
      ninjaTwo.age = 45;
    };

    return {
      name,
      age,
      // referenceIT,
      handleClick,
      ninjaOne,
      updateNinjaOne,
      ninjaTwo,
      updateNinjaTwo,
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
