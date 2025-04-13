<template>
    <div class="card">
        <div class="card_name">
            <h1>Hello! I'm Dep</h1>
        </div>
        <div class="card_content">
            <p>I am a cool person who develops shit from time to time.</p>
            <p>Currently, I am proficient in:</p>
            <div v-for="lang in LANGUAGES" class="Languages">
              <div class="Lang">
                <h1>{{ lang.name }}</h1>
                <p>{{ lang.description }}</p>
              </div>
            </div>
        </div>
    </div></template>

<script lang="ts" setup>

const LANGUAGES = [{name: 'Python 3', description:"Bery gug yes"}]

</script>

<style>
[class='card'] {
  margin: 5%;
  color: #FFFFFF;
  border-radius: 30px;
  border-color: #FFFFFF;
  border-style: solid;
  border-width: 25%;
}

[class='card_name'] {
  text-align: center;
  border-bottom: #FFFFFF99;
  border-bottom-width: 25%;
  border-bottom-style: dashed;
}

[class='card_content'] {
  margin-left: 5%;
  text-align: left 5%;
}

[class='Languages']{
  position: inherit;
  align-self: center;
}
</style>