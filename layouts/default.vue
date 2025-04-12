<template>
  <button class="bg_toggle" id='bg_button' @click="onclick">
    ⚙
  </button>
</template>

<script lang="ts" setup>
var lighting = false;

var item_color;

const DARKMODE = '#000000'
const WHITEMODE = '#FFFFFF'


function onclick() {
  if (lighting == true) {
   lighting = false;
  }else{
  lighting = true;
  };

  if (lighting == true) {
    document.fgColor = item_color = WHITEMODE;
    document.bgColor = DARKMODE;
  }
  else{  
    item_color = DARKMODE;
    document.bgColor = WHITEMODE;
  };

  var button = document.getElementById('bg_button');
  if (button != null){
    
    button.style.backgroundColor = item_color;
    button.style.color = document.bgColor;
  };
  return;
}

</script>

<style>
[class='bg_toggle'] {
  position: fixed;
  color: #FFFFFF;
  background-color: #000000;
  align-items: flex-start;
  border-radius: 25px;
  width: 50px;
  height: 50px;
  right: 1%;
  bottom: 1%;
  font-size: 25px;

}
</style>