<template>
  <div id="app">
    <img id="foto" v-bind:src="pictureBG"/>

    <img v-on:click="loopVooruit()" v-on:mouseenter="light('up')" v-on:mouseout="dark('up')"
         id="arrowUp" v-bind:src="pictureUp"/>

    <img v-on:click="kijkLinks()" v-on:mouseenter="light('left')" v-on:mouseout="dark('left')"
         id="arrowLeft" v-bind:src="pictureLeft"/>

    <img v-on:click="kijkRechts()" v-on:mouseenter="light('right')" v-on:mouseout="dark('right')"
         id="arrowRight" v-bind:src="pictureRight"/>

    <img v-on:click="loopAchteruit()" v-on:mouseenter="light('down')" v-on:mouseout="dark('down')"
         id="arrowDown" v-bind:src="pictureDown"/>

  </div>
</template>

<script>

import rondleidingData from '../src/data/rondleidingData'

export default
{
    name: 'app',
    data() {
      return{
        rondleidingData,
        pictureUp: 'pictures/arrowButtons/btnUp.png',
        pictureLeft: 'pictures/arrowButtons/btnLeft.png',
        pictureRight: 'pictures/arrowButtons/btnRight.png',
        pictureDown: 'pictures/arrowButtons/btnDown.png',
        position:0,
        pictureBG: rondleidingData.plaatsen[0].imgVoor,
        aantalPlaatsen: rondleidingData.plaatsen.length - 1
      }
    },
    methods: {
      light(richting)
      {
        if (richting === 'up'){this.pictureUp = 'pictures/arrowButtons/btnUpLight.png'}
        else if (richting === 'down'){this.pictureDown = 'pictures/arrowButtons/btnDownLight.png'}
        else if (richting === 'right'){this.pictureRight = 'pictures/arrowButtons/btnRightLight.png'}
        else if (richting === 'left'){this.pictureLeft = 'pictures/arrowButtons/btnLeftLight.png'}
      },
      dark(richting)
      {
        if (richting === 'up'){this.pictureUp = 'pictures/arrowButtons/btnUp.png'}
        else if (richting === 'down'){this.pictureDown = 'pictures/arrowButtons/btnDown.png'}
        else if (richting === 'right'){this.pictureRight = 'pictures/arrowButtons/btnRight.png'}
        else if (richting === 'left'){this.pictureLeft = 'pictures/arrowButtons/btnLeft.png'}
      },
      loopVooruit()
      {
        if (this.position < this.aantalPlaatsen)
        {
          this.position++,
          this.pictureBG = rondleidingData.plaatsen[this.position].imgVoor
        }
      },
      loopAchteruit()
      {
        if (this.position > 0)
        {
          this.position--,
          this.pictureBG = rondleidingData.plaatsen[this.position].imgVoor
        }
      },
      kijkRechts()
      {
        this.pictureBG = rondleidingData.plaatsen[this.position].imgRechts,
        setTimeout(()=>
        {
          this.pictureBG = rondleidingData.plaatsen[this.position].imgVoor
        }, 2000)
      },
      kijkLinks()
      {
        this.pictureBG = rondleidingData.plaatsen[this.position].imgLinks
        setTimeout(()=>
        {
          this.pictureBG = rondleidingData.plaatsen[this.position].imgVoor
        }, 2000)
      }
    },
    computed:{
    }

}
</script>

<style>
#foto
{
  height:100%;
  width:100%;
}
#arrowUp
{
  top: 20%;
  left: 48%;
  position:absolute;
  cursor:pointer;
  height:50px;
  width:50px;
}
#arrowLeft
{
  top: 50%;
  left: 15%;
  position:absolute;
  cursor:pointer;
  height:50px;
  width:50px;
}
#arrowRight
{
  top: 50%;
  left: 80%;
  position:absolute;
  cursor:pointer;
  height:50px;
  width:50px;
}
#arrowDown
{
  top: 80%;
  left: 48%;
  position:absolute;
  cursor:pointer;
  height:50px;
  width:50px;
}

</style>
