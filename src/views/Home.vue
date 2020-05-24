<template lang="pug">
.home
  .pianoWrapper
    piano
</template>

<script>
// @ is an alias to /src
import piano from "../components/svg/piano";

export default {
  name: "Home",
  components: { piano },
};
</script>
<style lang="scss" scoped>
.pianoWrapper {
  position: relative;
}
</style>
