<script setup lang="ts">
import SlotCard from "./components/SlotCard.vue";
</script>

<template>
  <SlotCard>
    <div>
      <slot name="header">test</slot>
      <slot>22</slot>
      <slot name="footer">footer</slot>
    </div>
  </SlotCard>
  <SlotCard>
    <div>
      <slot name="header"
        ><h4 style="background-color: green">new header</h4></slot
      >
      <slot><p>lipsum</p></slot>
      <slot name="footer"
        ><img
          src="https://www.google.com/logos/doodles/2021/seasonal-holidays-2021-6753651837109324-s.png"
      /></slot>
    </div>
  </SlotCard>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
