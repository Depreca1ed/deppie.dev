<template>
<div class="flex flex-col m-[5%] gap-y-10 items-center justify-center h-max">
  <div class='flex md:flex-row flex-col flex-warp items-center justify-center gap-y-10 w-full'>
    <img class="flex size-[50%] md:size-[25%] rounded-full outline-2 outline-offset-4 outline-[#cba6f7]/25" :src=userdata.avatar.path>
    <div class='flex flex-col gap-y-5 items-center'>
      <p class='font-bold text-5xl'>{{userdata.username}}</p>

      <hr class='flex border border-[#cba6f7]/25 size-auto w-[75%]'>

      <div class='flex flex-row self-center items-center justify-center' v-for="i, social in userdata.socials">
        <a class="flex self-center items-center justify-center" :href=i>
          <span class="flex items-center justify-center size-[10%] rounded-full hover:outline-2 outline-offset-4 outline-[#f38ba8]/50">
            <img class="invert" :src=social :href=i>
          </span>
        </a>
      </div>

    </div>
  </div>
  <hr class='flex border border-[#cba6f7]/25 size-auto w-[75%]'>
  <div class='flex items-center justify-center w-[90%]'>
    <p class='text-xl'>
    {{userdata.about}}
    </p>
  </div>
</div>
</template>

<script lang='ts' setup>
  const userdata = {
    "username": "Deppie",
    "avatar": {
      "path": "avatar.png"
    },
    "socials":{"github.png": "https://github.com/Depreca1ed",},
    "about": "I love thighs.",
  };
</script>

<style>
</style>
