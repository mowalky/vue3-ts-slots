<script setup lang="ts">
import { ref } from "vue";
import SlotCard from "./components/SlotCard.vue";
import Job from "./types/Job";

const jobs = ref<Job[]>([
  {
    title: "Developer",
    location: "NY",
    description: "Freelance",
    company: "Google",
    url: "https://google.com",
  },
]);

const addJob = (newJob: Job) => {
  jobs.value.push(newJob);
};

const removeJob = (index: number) => {
  jobs.value.splice(index, 1);
};
</script>

<template>
  <SlotCard>
    <div>
      <slot name="header">test</slot>
      <slot
        ><ul
          @dblclick="removeJob(i)"
          v-for="({ title, location }, i) in jobs"
          :key="title"
        >
          <li>{{ i }}. {{ title }} - {{ location }}</li>
        </ul></slot
      >
      <slot name="footer">footer</slot>
    </div>
  </SlotCard>
  <SlotCard>
    <div>
      <slot name="header"
        ><h4 style="background-color: green">new header</h4></slot
      >
      <slot
        ><p>lipsum</p>
        <button
          @click="
            addJob({
              title: 'new job' + Math.random(),
              location: 'new location',
              description: 'new description',
              company: 'new company',
              url: 'new url',
            })
          "
        >
          add job
        </button></slot
      >
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
