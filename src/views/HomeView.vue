<template>
  <div class="home">
    <h2>Refs</h2>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
    <button @click="age++">Increase age</button>
    <input type="text" v-model="name" />
    <br />
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update ninja two</button>
    <br />
    <h2>Computed</h2>
    <input type="text" v-model="search" />
    <div v-for="firstName in matchingNames" :key="firstName">
      {{ firstName }}
    </div>
    <button @click="handleStop">Stop watch</button>
  </div>
  <br />
  <h2>Props</h2>
  <PostList :posts="posts" />
</template>

<script>
import PostList from "../components/PostList.vue";
import { ref, reactive } from "@vue/reactivity";
import { computed, watch, watchEffect } from "@vue/runtime-core";

export default {
  name: "HomeView",
  components: { PostList },
  setup() {
    //refs
    const p = ref(null);
    const name = ref("Frank");
    const age = ref(15);
    const search = ref("");
    const firstNames = ref([
      "mario",
      "yoshi",
      "luigi",
      "toad",
      "bowser",
      "koopa",
      "peach",
    ]);
    const posts = ref([
      {
        title: "Welcome to blog",
        body: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam omnis, necessitatibus reprehenderit autem natus quisquam quis dolor. Fugiat odit dolore quod aperiam non, doloremque odio consequuntur, laborum beatae, nam impedit.",
        id: 1,
      },
      {
        title: "top 5 css tips",
        body: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam omnis, necessitatibus reprehenderit autem natus quisquam quis dolor. Fugiat odit dolore quod aperiam non, doloremque odio consequuntur, laborum beatae, nam impedit.",
        id: 2,
      },
    ]);

    //reactive
    const ninjaTwo = reactive({ name: "luigi", age: 35 }); //we can't use primitive values with reactive

    //computed
    const matchingNames = computed(() => {
      return firstNames.value.filter((firstName) =>
        firstName.toLowerCase().includes(search.value.toLowerCase())
      );
    });

    //methods
    const handleClick = () => {
      name.value = "luigi";
      age.value = 35;
      p.value.classList.add("test");
    };
    const updateNinjaTwo = () => {
      ninjaTwo.age = 45;
    };

    const handleStop = () => {
      stopWatch();
      stopEffect();
    };

    //watch, watchEffect and stopWatch/stopEffect
    const stopWatch = watch(search, () => {
      console.log("watch function ran");
    });

    const stopEffect = watchEffect(() => {
      console.log("watchEffect ran", search.value); //it runs any its dependencies(search.value) changes
    });

    //register
    return {
      name,
      age,
      handleClick,
      p,
      ninjaTwo,
      updateNinjaTwo,
      firstNames,
      search,
      matchingNames,
      stopWatch,
      stopEffect,
      handleStop,
      posts,
    };
  },
};
</script>
