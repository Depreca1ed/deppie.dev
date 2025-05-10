<template>
  <div>
    <div class="flex flex-col mx-auto mt-10 gap-y-10">
      <img class="place-self-center size-48"
        src="https://yt3.googleusercontent.com/79BJqnTubpfXZBrfuaztTOHZruh6Mih3S03HgiypklUwHgCUOyrlJsU5Xopd4ABQty-61WDQtxA=s1200">
      <p class="text-pretty md:text-balance font-bold self-center text-5xl hover:underline">
        <a href="https://music.youtube.com/playlist?list=PLAhyFk0kU8Q0Fgb51u-nglgP43siXnTur">
          {{ playlist.title }}
        </a>
      </p>
      <div class="flex flex-row self-center gap-x-5">
        <p class="text-2xl self-center">By</p>
        <div class="border-2 rounded-4xl border-black hover:border-white">
          <a :href=playlist.author.id>
            <div class="flex flex-row gap-x-4 m-1">
              <img class="size-14 rounded-4xl" :src=playlist.author.avatar>
              <p class="font-semibold text-center mx-auto my-auto text-3xl"> {{ playlist.author.name }}</p>
            </div>
          </a>
        </div>
      </div>
      <div v-for="song, index in songs" class="mt-10 mx-auto">
        <button class="rounded-2xl border-4 border-black hover:border-white" @click=onclick(index)>
          <div class="flex flex-col gap-y-5 w-300">
            <div class="flex flex-row gap-x-5 w-300 m-1">
              <img class="size-24 rounded-2xl self-start" :src=song.cover>
              <div class="flex flex-col gap-y-2.5 self-center text-left">
                <p class="text-pretty md:text-balance font-bold">{{ song.title }}</p>
                <p class="font-semibold text-gray-400">{{ song.creator }}</p>
              </div>
            </div>
            <p class="text-pretty md:text-balance ml-10 text-left" v-if="song.show">{{ song.review }}</p>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>

  const playlist = {
    "title": "These Girl Bands wont make you cry",
    "author": {
      "name": "raeschh",
      "id": "https://discord.com/users/257904697032179712",
      "avatar": "https://cdn.discordapp.com/avatars/257904697032179712/e34f0a38042a8c4c34359ce65b10f9f0.png"
    }
  }

  type Song = {
    title: string,
    creator: string,
    url: string,
    cover: string,
    show: boolean,
    review: string
  }

  const songs = ref<Record<number, Song>>({
    1: {
      "title": '青い春と西の空-instrumental- - Blue Spring and Western Sky-instrumental-',
      "creator": "kessoku band",
      "url": "https://music.youtube.com/watch?v=BGtGRP73iR4&si=2DuykFFoDloURmht",
      "cover": "https://lh3.googleusercontent.com/HO9-1DmMU29j6JtY-4f8DxKkD1WB7EMTVxGQm6ZvtAClmsbp1AvXeu76WfTNZRt9XJXI-6CMjZSoEo4=w544-h544-l90-rj",
      "show": false,
      "review": "This song felt really calm while also maintaining the rock feel overall, which personally I'm a fan of. It doesn't bring a lot of energy by itself but I would listen a lot just for the calm vibe it gives off.\n\n4/5",
    },
    2: {
      "title": 'あのバンド - That band',
      "creator": "kessoku band",
      "url": "https://music.youtube.com/watch?v=MtuFP3Tl1kE&si=OyjBTrB3blOgyZGw",
      "cover": "https://lh3.googleusercontent.com/AniPdO57l8shB2EWKPxpwtllogUjm5rRjibnlDre3PlgqIoiyVRWj6FHr9de2OC7ONIDHj_59bG-cShR=w544-h544-l90-rj",
      "show": false,
      "review": "Hello",
    },
    3: {
      "title": 'milky way',
      'creator': 'kessoku band',
      "url": "https://music.youtube.com/watch?v=LaZIDFaobMU&si=QCCsr3dMfA-tANmG",
      "cover": 'https://lh3.googleusercontent.com/nQJ0-XsU7BjKhyumiWKo9bjHBH_FlDcG8zyShFzkE5bQSNJWQM5VGG85qtQBx_HX_-GUaTeVqznFBLI=w544-h544-l90-rj',
      "show": false,
      "review": "Hello",
    },
    4: {
      "title": 'UNITE',
      'creator': 'kessoku band',
      "url": "https://music.youtube.com/watch?v=FnhedPLxksQ&si=steFR2MA77MiGGP7",
      "cover": "https://lh3.googleusercontent.com/nQJ0-XsU7BjKhyumiWKo9bjHBH_FlDcG8zyShFzkE5bQSNJWQM5VGG85qtQBx_HX_-GUaTeVqznFBLI=w544-h544-l90-rj",
      "show": false,
      "review": "PEAK"
    },
    5: {
      "title": "KiLLKiSS",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=RexyoaXaQ1o&si=F8MohO6zmUtIBbt_",
      "cover": "https://lh3.googleusercontent.com/pgle3mgY4mhhXkF611bJkrv-oU2FX-YBxXp35mhnQwLxCvP8qL9FfDNCu1RM4Jcq-TVgAAd0fRjBx7OQrg=w544-h544-l90-rj",
      "show": false,
      "review": "EVEN PEAKER",
    },
    6: {
      "title": "Imprisoned XII",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=3RJuUtGL73U&si=tIDhPZprlRnTpc1z",
      "cover": "https://lh3.googleusercontent.com/Q4ods7wwFwFz1oi5pw_eTVPkAIPkmwVzOtrDEybPfmzvRWsxHGRoWuB6o9FrH0mieJOg5wxuoTAx5kDcTA=w544-h544-l90-rj",
      "show": false,
      "review": "EVEN PEAKER",
    },
    7: {
      "title": "Ether",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=9Dl4Ec0Mlak&si=Ng4hZIS7n8ScPRXy",
      "cover": "https://lh3.googleusercontent.com/l814cWdM1nB6v3D_-qk_AFSnAAPBkYKUY6kvq9u74CxtSpA81lSu5b9UwyYTtAfHQSNK-ffXskSUqjW5=w544-h544-l90-rj",
      "show": false,
      "review": "EVEN PEAKER",
    },

  })

  function onclick(song: number) {
    console.log("Hi");
    songs.value[song].show = !songs.value[song].show
  }
</script>
<style>
  body {
    background-color: #000000;
    color: #FFFFFF;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
</style>
