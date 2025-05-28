<template>
  <div class="flex flex-col mt-10 gap-y-10">
    <img class="place-self-center size-48"
      src="https://yt3.googleusercontent.com/79BJqnTubpfXZBrfuaztTOHZruh6Mih3S03HgiypklUwHgCUOyrlJsU5Xopd4ABQty-61WDQtxA=s1200">
    <p class="text-pretty md:text-balance font-bold self-center text-2xl hover:underline">
      <a href="https://music.youtube.com/playlist?list=PLAhyFk0kU8Q0Fgb51u-nglgP43siXnTur">
        {{ playlist.title }}
      </a>
    </p>
    <div class="flex flex-row self-center gap-x-5">
      <p class="text-2xl self-center">By</p>
      <div class="border-2 rounded-4xl border-black hover:border-white">
        <a :href=playlist.author.id>
          <div class="flex flex-row gap-x-4">
            <img class="size-14 rounded-4xl" :src=playlist.author.avatar>
            <p class="font-semibold text-center mx-screen my-auto text-3xl"> {{ playlist.author.name }}</p>
          </div>
        </a>
      </div>
    </div>
    <div v-for="song, index in songs" class="w-screen md:w-[75%] h-auto mt-10 justify-center md:mx-auto mx-screen">
      <button class="rounded-2xl border-2 w-[100%] border-black hover:border-white" @click=onclick(index)>
        <div class="flex flex-col gap-y-5">
          <div class="flex flex-row gap-x-5">
            <img class="size-24 rounded-2xl self-start" :src=song.cover>
            <div class="flex flex-col gap-y-2.5 text-left">
              <p class="text-pretty md:text-balance font-bold hover:underline"><a :href=song.url>{{ song.title }}</a>
              </p>
              <p class="font-semibold text-gray-400">{{ song.creator }}</p>
            </div>
          </div>
          <div v-if=song.show>
            <p class="text-pretty text-left ml-5 w-[100% - 10] self-center">{{ song.review }}</p>
            <p class="font-bold text-5xl self-center">{{ song.score }}</p>
          </div>
        </div>
      </button>
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
    score: string,
    review: string
  }

  const songs = ref<Record<number, Song>>({
    1: {
      "title": '青い春と西の空-instrumental- - Blue Spring and Western Sky-instrumental-',
      "creator": "kessoku band",
      "url": "https://music.youtube.com/watch?v=BGtGRP73iR4&si=2DuykFFoDloURmht",
      "cover": "https://lh3.googleusercontent.com/HO9-1DmMU29j6JtY-4f8DxKkD1WB7EMTVxGQm6ZvtAClmsbp1AvXeu76WfTNZRt9XJXI-6CMjZSoEo4=w544-h544-l90-rj",
      "show": false,
      "score": "4/5",
      "review": "This song felt really calm while also maintaining the rock feel overall, which personally I'm a fan of. It doesn't bring a lot of energy by itself but I would listen a lot just for the calm vibe it gives off.",
    },
    2: {
      "title": 'あのバンド - That band',
      "creator": "kessoku band",
      "url": "https://music.youtube.com/watch?v=MtuFP3Tl1kE&si=OyjBTrB3blOgyZGw",
      "cover": "https://lh3.googleusercontent.com/AniPdO57l8shB2EWKPxpwtllogUjm5rRjibnlDre3PlgqIoiyVRWj6FHr9de2OC7ONIDHj_59bG-cShR=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "DEFINITELY ONE OF THE BEST SONGS OF THE ALBUM ITS PART OF. HOLY PEAK. The vocals and rock blends amazingly well to the point where finding any criticism for it is difficult and it gets bonus points for sounding encouraging. I wuv it",
    },
    3: {
      "title": 'milky way',
      'creator': 'kessoku band',
      "url": "https://music.youtube.com/watch?v=LaZIDFaobMU&si=QCCsr3dMfA-tANmG",
      "cover": 'https://lh3.googleusercontent.com/nQJ0-XsU7BjKhyumiWKo9bjHBH_FlDcG8zyShFzkE5bQSNJWQM5VGG85qtQBx_HX_-GUaTeVqznFBLI=w544-h544-l90-rj',
      "show": false,
      "score": "5/5",
      "review": "Hello",
    },
    4: {
      "title": 'UNITE',
      'creator': 'kessoku band',
      "url": "https://music.youtube.com/watch?v=FnhedPLxksQ&si=steFR2MA77MiGGP7",
      "cover": "https://lh3.googleusercontent.com/nQJ0-XsU7BjKhyumiWKo9bjHBH_FlDcG8zyShFzkE5bQSNJWQM5VGG85qtQBx_HX_-GUaTeVqznFBLI=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "PEAK"
    },
    5: {
      "title": "KiLLKiSS",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=RexyoaXaQ1o&si=F8MohO6zmUtIBbt_",
      "cover": "https://lh3.googleusercontent.com/pgle3mgY4mhhXkF611bJkrv-oU2FX-YBxXp35mhnQwLxCvP8qL9FfDNCu1RM4Jcq-TVgAAd0fRjBx7OQrg=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    6: {
      "title": "Imprisoned XII",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=3RJuUtGL73U&si=tIDhPZprlRnTpc1z",
      "cover": "https://lh3.googleusercontent.com/Q4ods7wwFwFz1oi5pw_eTVPkAIPkmwVzOtrDEybPfmzvRWsxHGRoWuB6o9FrH0mieJOg5wxuoTAx5kDcTA=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    7: {
      "title": "Ether",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=9Dl4Ec0Mlak&si=Ng4hZIS7n8ScPRXy",
      "cover": "https://lh3.googleusercontent.com/l814cWdM1nB6v3D_-qk_AFSnAAPBkYKUY6kvq9u74CxtSpA81lSu5b9UwyYTtAfHQSNK-ffXskSUqjW5=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    8: {
      "title": "メリトクラシー - Meritocracy",
      'creator': 'LAURELEY(Mizukami Sui)',
      "url": "https://music.youtube.com/watch?v=2Eu4CSJ93kM&si=-145n_tgO06GGht0",
      "cover": "https://lh3.googleusercontent.com/P54wzAyroU3u5lZRmpW7j47eTKWYSKjt1dh7uOKrZyQhkUsOzE5Fiu4IdKFYrhFCA0g6fY-bTf6uV3xl=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    9: {
      "title": "雑踏、僕らの街 - Wrong World",
      'creator': 'TOGENASHI TOGEARI',
      "url": "https://music.youtube.com/watch?v=hfRSZyUuwIk&si=q1dolydKzMffIxue",
      "cover": "https://lh3.googleusercontent.com/iyu6L7GTYsdvmKQpBZjDbkJUG1aNsvBhOnIgv5KCI6tCM_gQVhuLemsp5ZcL2EUAjZcE-HMcNhm1FcdASg=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    10: {
      "title": "誰にもなれない私だから - I'm Nobody",
      'creator': 'TOGENASHI TOGEARI',
      "url": "https://music.youtube.com/watch?v=dJottC7FmYc&si=-ZVaB3POrr7jKcRJ",
      "cover": "https://lh3.googleusercontent.com/ef5re79DZ8Mma6S0ckONj87HHi6_qFxX1JcOORqhV0lyc6rxPX40zH19snPy34aJ9emdZm35xYBqG5rTlw=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    11: {
      "title": "偽りの理 - no rhyme nor reason",
      'creator': 'TOGENASHI TOGEARI',
      "url": "https://music.youtube.com/watch?v=aIgSVT6U49A&si=PFMDkBsHQoKCL3R8",
      "cover": "https://lh3.googleusercontent.com/pl2ewg-M18JZmcOB5qhzWubZUOtRt73ek1-ls6mY5fcARE6hhMGo6CVLeN6DfMscTPedkSGy3D0VKHf1=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    12: {
      "title": "壱雫空 - Hitoshizuku",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=bqDL0mTUiLs&si=I3e7U6uAWmUVaCeR",
      "cover": "https://lh3.googleusercontent.com/sC2Vr-kQrJbdPnb2PyoGRb6kXQDadDngDFufUQS-HT-Itg9SKMIoRyKRODMSUqt1GfpVElNBUHZc8KM=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    13: {
      "title": "春日影 (MyGO!!!!! ver.) - Haruhikage (MyGO!!!!! ver.)",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=NycFr6D6DSw&si=d2Bycp3aj905UEF9",
      "cover": "https://lh3.googleusercontent.com/NK_v245J52vq2Wx1g8GJGRqHQBaxZj65bzl0j25sx_08aIo8Rc_7U5A07de3NUq2l3TtapnK_AuLwVcl=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    14: {
      "title": "影色舞 - SilhouetteDance",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=5_ZWx7Q26Tw&si=vyfBOlRHrtH4Ek7-",
      "cover": "https://lh3.googleusercontent.com/zlhsEUJAk5LwKIm81UKkJfj3drraavEkcjV2StHaRWQFsYoxbvskqYRyFekwSvSaca0iQCmgdg-shuvMuw=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },
    15: {
      "title": "迷星叫 (instrumental) - Mayoiuta (instrumental)",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=uyC45EQb4dM&si=Op7gyhiAn4aBf7SD",
      "cover": "https://lh3.googleusercontent.com/iV4bgifkW_75FO-huG3c06U32_Q72KmKcTobLxNASY3zpYjY9bFtJs9gK-h8c91-KfgDVSec0b2KvN04=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "EVEN PEAKER",
    },

  })
  function onclick(song_index: number) {

    songs.value[song_index].show = !songs.value[song_index].show
  }
</script>
<style>
  body {
    background-color: #000000;
    color: #FFFFFF;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  html {
    background-color: #000000;
    background: none;
    color: #FFFFFF;

  }
</style>
