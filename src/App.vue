<template>
  <div id="app" class="p-5 m-auto w-100">
    <h1>Anagrammert</h1>
    <words/>
  </div>
</template>

<script>
import Words from "./components/Words";

export default {
  name: "App",
  components: {
    Words
  }
};
</script>