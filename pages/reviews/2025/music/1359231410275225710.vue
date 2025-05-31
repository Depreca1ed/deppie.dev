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
      <p class="text-2xl self-center">Made by</p>
      <div class="border-2 rounded-4xl border-black hover:border-white">
        <a :href=playlist.author.id>
          <div class="flex flex-row gap-x-4">
            <img class="size-14 rounded-4xl" :src=playlist.author.avatar>
            <p class="font-semibold text-center mx-screen my-auto text-3xl"> {{ playlist.author.name }}</p>
          </div>
        </a>
      </div>
    </div>
    <div class="flex flex-row self-center gap-x-5">
      <p class="text-2xl self-center">Reviewed by</p>
      <div class="border-2 rounded-4xl border-black hover:border-white">
        <a :href=playlist.reviewer.id>
          <div class="flex flex-row gap-x-4">
            <img class="size-14 rounded-4xl" :src=playlist.reviewer.avatar>
            <p class="font-semibold text-center mx-screen my-auto text-3xl"> {{ playlist.reviewer.name }}</p>
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
            <p class="text-pretty text-left ml-5 w-[95%] self-center">{{ song.review }}</p>
            <p class="font-bold text-5xl self-center">{{ song.score }}</p>
          </div>
        </div>
      </button>
    </div>
    <div class="flex border-1 border-amber-300 bg-gray-900 text-gray-400 self-center w-[50%] rounded-t-3xl">
      <p class="text-center self-center mx-auto">
        If thou thinketh the review is shit, its because I suck at writing reviews.
      </p>
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
    },
    "reviewer": {
      "name": "deprecating",
      'id': "https://discord.com/users/688293803613880334",
      "avatar": "https://cdn.discordapp.com/avatars/688293803613880334/793949f5865d7e312827ada3458458ef.png"
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
      "review": "My personal most favourite song from the band. It syncronises the drums and vocals really well and the whole beat feels really positive. I would fight the world to defend this song fr fr.",
    },
    4: {
      "title": 'UNITE',
      'creator': 'kessoku band',
      "url": "https://music.youtube.com/watch?v=FnhedPLxksQ&si=steFR2MA77MiGGP7",
      "cover": "https://lh3.googleusercontent.com/nQJ0-XsU7BjKhyumiWKo9bjHBH_FlDcG8zyShFzkE5bQSNJWQM5VGG85qtQBx_HX_-GUaTeVqznFBLI=w544-h544-l90-rj",
      "show": false,
      "score": "4/5",
      "review": "The song sounds very aggressive and handles it really well, the chorus especially. It sounds like a burst and then it follows it with a really calm sound after going back to being aggressive. It's a good song to vibe to."
    },
    5: {
      "title": "KiLLKiSS",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=RexyoaXaQ1o&si=F8MohO6zmUtIBbt_",
      "cover": "https://lh3.googleusercontent.com/pgle3mgY4mhhXkF611bJkrv-oU2FX-YBxXp35mhnQwLxCvP8qL9FfDNCu1RM4Jcq-TVgAAd0fRjBx7OQrg=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "The song was my first impression of this band, which was they are very aggressive with the sounds. While it calms down on the being aggressive part, the chorus and the part after it is what really attracts me to it. The song also reminds me of................... Yharon's song.... the boss from terraria calamity mod",
    },
    6: {
      "title": "Imprisoned XII",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=3RJuUtGL73U&si=tIDhPZprlRnTpc1z",
      "cover": "https://lh3.googleusercontent.com/Q4ods7wwFwFz1oi5pw_eTVPkAIPkmwVzOtrDEybPfmzvRWsxHGRoWuB6o9FrH0mieJOg5wxuoTAx5kDcTA=w544-h544-l90-rj",
      "show": false,
      "score": "4/5",
      "review": "Compared to the previous song's speed and emotion(the sound one not the lyrics if yk what i mean), this felt like a change.... too big of a change. I personally love it a lot since I love calm rock songs but even if I didn't, it sounds beautiful.",
    },
    7: {
      "title": "Ether",
      'creator': 'Ave Mujica',
      "url": "https://music.youtube.com/watch?v=9Dl4Ec0Mlak&si=Ng4hZIS7n8ScPRXy",
      "cover": "https://lh3.googleusercontent.com/l814cWdM1nB6v3D_-qk_AFSnAAPBkYKUY6kvq9u74CxtSpA81lSu5b9UwyYTtAfHQSNK-ffXskSUqjW5=w544-h544-l90-rj",
      "show": false,
      "score": "10/10",
      "review": "My initial impression was highly negetive due to being under the assumption that the vocals and instruments are wrongly syncronised. This was very wrong which I later realised. Aside from that, the song feels like a combination of the previous 2 songs combined to an semi-aggresive tone. I've grown to like this song more the more I listen to it. Another thing I must add is that it sounds strangely simple in its tone, like the opposite of being sensory overloaded with sounds.",
    },
    8: {
      "title": "メリトクラシー - Meritocracy",
      'creator': 'LAURELEY(Mizukami Sui)',
      "url": "https://music.youtube.com/watch?v=2Eu4CSJ93kM&si=-145n_tgO06GGht0",
      "cover": "https://lh3.googleusercontent.com/P54wzAyroU3u5lZRmpW7j47eTKWYSKjt1dh7uOKrZyQhkUsOzE5Fiu4IdKFYrhFCA0g6fY-bTf6uV3xl=w544-h544-l90-rj",
      "show": false,
      "score": "4/5",
      "review": "The song puts the rock in the rock..... Bad joke I know but it sounds a bit generic. Not much which really highlighted to me other than the chorus which sounds so good like wtf? The chorus peaks in h=the vibe factor to me.",
    },
    9: {
      "title": "雑踏、僕らの街 - Wrong World",
      'creator': 'TOGENASHI TOGEARI',
      "url": "https://music.youtube.com/watch?v=hfRSZyUuwIk&si=q1dolydKzMffIxue",
      "cover": "https://lh3.googleusercontent.com/iyu6L7GTYsdvmKQpBZjDbkJUG1aNsvBhOnIgv5KCI6tCM_gQVhuLemsp5ZcL2EUAjZcE-HMcNhm1FcdASg=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. I love togetoge. \n\nOkay seriously, when I first listened to it and when I first saw the scene for it, I felt the goosebumps. It nails every part it could nail especially the chorus which sounds just right. Considering the encourging nature of the song, it nails even that.",
    },
    10: {
      "title": "誰にもなれない私だから - I'm Nobody",
      'creator': 'TOGENASHI TOGEARI',
      "url": "https://music.youtube.com/watch?v=dJottC7FmYc&si=-ZVaB3POrr7jKcRJ",
      "cover": "https://lh3.googleusercontent.com/ef5re79DZ8Mma6S0ckONj87HHi6_qFxX1JcOORqhV0lyc6rxPX40zH19snPy34aJ9emdZm35xYBqG5rTlw=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "I love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love love togetoge so much\n\nI would listen to this song a million times and I still wouldn't get bored of it istg. The instruments in the chorus execute an amazing burst when it starts and then the vocals accompany it perfectly. The sad+encouraging nature of the sounds is also maintained throughout the song and it never drops it. It's so peak.",
    },
    11: {
      "title": "偽りの理 - no rhyme nor reason",
      'creator': 'TOGENASHI TOGEARI',
      "url": "https://music.youtube.com/watch?v=aIgSVT6U49A&si=PFMDkBsHQoKCL3R8",
      "cover": "https://lh3.googleusercontent.com/pl2ewg-M18JZmcOB5qhzWubZUOtRt73ek1-ls6mY5fcARE6hhMGo6CVLeN6DfMscTPedkSGy3D0VKHf1=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "I lov- Okay I wont do that again. Another blend of semi-aggresive and calm tune, although I would say the vocals blend a little too well with instrumentals but doesn't sound wrong. It has a great vibe overall and doesn't present anything to disliked in it",
    },
    12: {
      "title": "壱雫空 - Hitoshizuku",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=bqDL0mTUiLs&si=I3e7U6uAWmUVaCeR",
      "cover": "https://lh3.googleusercontent.com/sC2Vr-kQrJbdPnb2PyoGRb6kXQDadDngDFufUQS-HT-Itg9SKMIoRyKRODMSUqt1GfpVElNBUHZc8KM=w544-h544-l90-rj",
      "show": false,
      "score": "4/5",
      "review": "The song's beat reminds me UNITE from kessoku band strangely enough. It bends more towards the generic ani-rock side in my opinion but sounds good enough. Not much to say really for this one.",
    },
    13: {
      "title": "春日影 (MyGO!!!!! ver.) - Haruhikage (MyGO!!!!! ver.)",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=NycFr6D6DSw&si=d2Bycp3aj905UEF9",
      "cover": "https://lh3.googleusercontent.com/NK_v245J52vq2Wx1g8GJGRqHQBaxZj65bzl0j25sx_08aIo8Rc_7U5A07de3NUq2l3TtapnK_AuLwVcl=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "I'd say this is my personal favourite from MyGO(ave mujica not included). It sounds sweet and calm and has a little bit of the rock factor in it. I love these kinds of songs",
    },
    14: {
      "title": "影色舞 - SilhouetteDance",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=5_ZWx7Q26Tw&si=vyfBOlRHrtH4Ek7-",
      "cover": "https://lh3.googleusercontent.com/zlhsEUJAk5LwKIm81UKkJfj3drraavEkcjV2StHaRWQFsYoxbvskqYRyFekwSvSaca0iQCmgdg-shuvMuw=w544-h544-l90-rj",
      "show": false,
      "score": "5/5",
      "review": "This sounds like an isekai OP.... It has a really nice vibe tho and the part after the chorus is really really good. The 'oooooooooooo' in the background also highlights to me and its one of the reasons I really enjoyed the songs. It still sounds like an isekai OP tho..... MyGO band members get isekaid and they have to sing to defeat the demon lord.... or just go the luminous witches route idfk.",
    },
    15: {
      "title": "迷星叫 (instrumental) - Mayoiuta (instrumental)",
      'creator': 'MyGO!!!!!',
      "url": "https://music.youtube.com/watch?v=uyC45EQb4dM&si=Op7gyhiAn4aBf7SD",
      "cover": "https://lh3.googleusercontent.com/iV4bgifkW_75FO-huG3c06U32_Q72KmKcTobLxNASY3zpYjY9bFtJs9gK-h8c91-KfgDVSec0b2KvN04=w544-h544-l90-rj",
      "show": false,
      "score": "3/5",
      "review": "Not much to say tbh...... It's..... instruments...... they sync good i guesss",
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
