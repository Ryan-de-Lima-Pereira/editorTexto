<template>
  <div class="center">
    <BaseTexto></BaseTexto>
  </div>
</template>

<script>
import BaseTexto from './components/BaseTexto.vue';

export default {
  components: {
    BaseTexto,
}
};
</script>

<style lang="sass">
*
  margin: 0
  padding: 0
  box-sizing: border-box

.center
  display: flex
  justify-content: center
  align-items: center
  height: 100vh
</style>
