<template>
  <div class="home">
    <p>My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  setup() {
    let name = "Frank";
    let age = 15;
    const handleClick = () => {
      console.log("you clicked me")
    }
    return { name: name, age: age, handleClick };
  },
};
</script>
