<template>
  <div class="flex flex-col mx-auto mt-10 max-w-max max-h-max gap-x-6 border-4 border-amber-50 rounded-3xl">
    <div class="flex flex-row flex-wrap items-center ">
      <img class="place-self-center m-10 size-48 rounded-4xl" :src=SOCIALS.primary.avatar>
      <div class="flex flex-col gap-y-5">
        <div class="w-96 text-center text-9xl font-bold">
          <p>{{ SOCIALS.primary.name }}</p>
        </div>
        <div class="text-center text-2xl font-semibold text-gray-500">
          <p>(Deprecated)</p>
        </div>
      </div>
    </div>
    <div class="flex border-t-1">
      <div class="text-center mx-5 text-2xl text-wrap font-semibold">
        <p>I love thighs..... A LOT</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const PRIMARY_USERNAME = "Depreca1ed"

const { data: gh_data } = await useFetch('https://api.github.com/users/' + PRIMARY_USERNAME);

const gh_data_value = gh_data.value as any

const SOCIALS = { 'primary': { 'name': gh_data_value.name, 'avatar': gh_data_value.avatar_url } }

</script>

<style></style>