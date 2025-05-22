<template>
  <div class="flex flex-col mx-auto">
    <div class="flex flex-col flex-wrap items-center mt-10 gap-5">
      <img class="place-self-center self-center size-auto rounded-4xl" :src=SOCIALS.primary.avatar>
      <div class="flex flex-col gap-y-5">
        <div class="text-center text-2xl font-semibold text-gray-300">
          <p>Hi, I am </p>
          <p class="font-bold text-white text-8xl">{{ SOCIALS.primary.name }}</p>
        </div>
        <div class="text-center text-2xl font-semibold text-gray-500">
          <p>(Deprecated)</p>
        </div>
      </div>
    </div>
    <div class="flex border-t-1">
      <div class="text-center mx-5 text-2xl text-wrap font-semibold">
        <p>I love thighs</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
  const SOCIALS = { 'primary': { 'name': "Dep", 'avatar': "https://avatars.githubusercontent.com/u/70801324" } }

</script>

<style>
  html {
    background: url(/assets/bg.webp);
    background-size: cover;
    background-repeat: no-repeat;
    background-blend-mode: darken;
    background-color: #000000b0;
  }
</style>