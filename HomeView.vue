<template>
    <button @click="startGameTimer()" v-if="lvl1 == 0 ">Start Level 1</button>
    <button @click="startGameTimer2()" v-if="lvl1 == 1 && lvl2 !=1">Start Level 2</button>
    <button @click="startGameTimer3()" v-if="lvl1 == 1 && lvl2 ==1">Start Level 3</button>
  <div class="gameWindow">
    <!-- Para os v-if -->
    <!-- existem 2 "screens" base, todas as outras screens sao baseados nos 2 screen base. todos os screens impares sao baseados no screen base1 e todos os pares no 2-->
    <!-- o "screenVar" serve para determinar qual o screen que sera usado -->
    
    <div class="gameGackground" v-if="tempoRestante == 32">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 31">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 30">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 29">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 28">
      <img src="../assets/gameScreens/rocks/screen_rock_l1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 27">
      <img src="../assets/gameScreens/rocks/screen_rock_l2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 26">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 25">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 24">
      <img src="../assets/gameScreens/puddle/puddle1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 23">
      <img src="../assets/gameScreens/puddle/puddle2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 22">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 21">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 20">
      <img src="../assets/gameScreens/granny/zebra_granny1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 19">
      <img src="../assets/gameScreens/granny/zebra_granny2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 18">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 17">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 16">
      <img src="../assets/gameScreens/rocks/screen_rock_r1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 15">
      <img src="../assets/gameScreens/rocks/screen_rock_r2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 14">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 13">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 12">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 11">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 10">
      <img src="../assets/gameScreens/granny/zebra_granny1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 9">
      <img src="../assets/gameScreens/granny/zebra_granny2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 8">
      <img src="../assets/gameScreens/rocks/screen_rock_r1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 7">
      <img src="../assets/gameScreens/rocks/screen_rock_r2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 6">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 5">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 4">
      <img src="../assets/gameScreens/puddle/puddle1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 3">
      <img src="../assets/gameScreens/puddle/puddle2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 2">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == 1">
      <img src="../assets/gameScreens/base2.png" alt="">
    </div>
    <div class="gameGackground" v-if="tempoRestante == -1">
      <img src="../assets/gameScreens/base1.png" alt="">
    </div>
    <!-- fim dos v-if -->

    <!-- relogio e vida -->
    <div id="relogio">
      {{ " Tempo: " + tempoRestante}}
      <br>
      {{ "Vidas: " + vidas + " &#10084;"}}
    </div>
      
    <!-- fim do relogio e vida -->

    <!-- Skater avatar -->
    <div id="vidaContainer">
      <div v-if="isRight == 1">
        <img id="skaterRight" src="../assets/gameScreens/rect.png" alt="">
      </div>
      <div v-if="isRight == 0">
        <img id="skaterLeft" src="../assets/gameScreens/rect.png" alt="">
      </div>
    </div>
    <!-- fim dos Skater avatar -->

    <div class="buttons">
      <button id="go" class="buttonsBackgroundColor"></button>

      <button id="left" v-on:click="isRight = 0" class="buttonsBackgroundColor"><img src="../assets/buttons/left.png"
          class="btimg"></button>
      <button id="stop" v-on:click="stopChanger()" class="buttonsBackgroundColor"><img src="../assets/buttons/stop.png" class="btimg"></button>

      <button id="right" v-on:click="isRight = 1"  class="buttonsBackgroundColor"><img src="../assets/buttons/right.png"
          class="btimg"></button>
      <button id="jump" v-on:click="jumpChanger()" class="buttonsBackgroundColor"><img src="../assets/buttons/jump.png" class="btimg"></button>
        
    </div>

  </div>

  <div v-if="test == 1" class="popup-game">
      <div class="popup-game2">
        <!-- Popup content here -->
        <div>
          <div class="alert alert-lose" role="alert">
            game over! :(
        <br>

          <button class="suc" @click="restart()">Restart</button>
        </div>
      </div>
    </div>
  </div>

  <div v-if="test == 2" class="popup-game">
      <div class="popup-game2">
        <!-- Popup content here -->
        <div>
          <div class="alert alert-lose" role="alert">
            You won! :D
        <br>
        <div class="jorge">
          <button class="suc" @click="test=0">Next Level</button>
        
          <button class="suc" @click="changeLevel()">Choose Level</button>
        </div>
      </div>
      </div>
    </div>
  </div>

  <div v-if="test == 3" class="popup-game">
      <div class="popup-game2">
        <!-- Popup content here -->
        <div>
          <div class="alert alert-lose" role="alert">
            You won! :D
        <br>
        <div class="jorge">
        
          <button class="suc" @click="changeLevel()">Choose Level</button>
        </div>
      </div>

      
      </div>
    </div>
  </div>

</template>



<script>



export default {
  
  data() {
    return {
      lvl1:0,
      lvl2:0,
      lvl3:5,

      test:0,
      playerPos: null,
      vidas: 30,
      funny: null,

      randomRoll: 0,

      obsticleAppear: 0,
      isRight: 0,
      isJump: 0,
      isStop: 0,

      currentTime: null,

      //for checkCollision method
      tempoRestante: 3,
      tempoLimite: 3,
      counter:0,
      intervalId: null,
      isColided: 0
    }
  },

  mounted() {
    this.startTimer();
    this.lvl1 = localStorage.getItem('lvl1')
    this.lvl2 = localStorage.getItem('lvl2')
    this.lvl3 = localStorage.getItem('lvl3')
  },

  methods: {
    nextLvl(){

    },

    changeLevel(){
      window.location = "http://127.0.0.1:5173/#/";
    },
    restart() {
      location.reload(); 
    },
    startTimer() { /* ignora esta funcao por completo*/
      this.timerInterval = setInterval(() => {
        if (++this.timeElapsed === this.timeLimit) {
          clearInterval(this.timerInterval);
        }
      }, this.timeClock);
    },


    rollForObsticle() {
      this.randomRoll = Math.floor(Math.random() * (15 - 5 + 1)) + 5 //minimo 5, maximo 15
      if (this.randomRoll > 10) {
        this.obsticleAppear = 1;
      }
      else this.obsticleAppear = 0;
    },

    stopChanger() {
      this.isStop = 1
    },
    jumpChanger() {
      this.isJump = 2
    },

    literally_the_whole_game(){
      if(this.tempoRestante > 0) {
        this.counter++
        this.tempoRestante = this.tempoLimite - this.counter

        if(this.isRight == 0 && this.tempoRestante == 26){
          this.vidas -= 1;
        }
        else if (this.isJump == 0 && this.tempoRestante == 22 ) {
          this.vidas -= 1;
        }
        else if (this.isStop == 0 && this.tempoRestante == 18) {
          this.vidas -= 1;
        }
        else if (this.isRight == 1 && this.tempoRestante == 14) {
          this.vidas -= 1;
        }
        else if (this.isStop == 0 && this.tempoRestante == 8) {
          this.vidas -= 1;
        }
        else if (this.isRight == 1 && this.tempoRestante == 6) {
          this.vidas -= 1;
        }
        else if (this.isJump == 0 && this.tempoRestante == 2 ) {
          this.vidas -= 1;
        }
      }
      if(this.tempoRestante == 0 || this.vidas == 0) {
        this.test = 1;
        this.tempoRestante = 0;
      }
      if(this.tempoRestante == 0 && this.vidas > 0) {
        this.tempoRestante = -1;
        this.test = 2;
        this.lvl1complete();
      }
    },

    lvl1complete() {
      if(this.lvl2 ==0 && this.lvl1 == 1){
          this.lvl2 = 1;
          localStorage.setItem('lvl2', 1)
        }
      else if(this.lvl1 ==0){
          this.lvl1 = 1;
          localStorage.setItem('lvl1', 1)
      }
        
    },
    resetStuff() {
      this.isJump -= 1;
      this.isStop -= 0;
    },
    startGameTimer() {
      this.intervalId = setInterval(this.checkCollision, 1000) //make sure this can only be pressed once per session
    },
    startGameTimer2() {
      this.tempoRestante= 30,
      this.tempoLimite= 30,
      clearInterval(this.intervalId)
      this.vidas=30,
      this.intervalId = setInterval(this.checkCollision, 500) //make sure this can only be pressed once per session
    },
    startGameTimer3(){
      localStorage.setItem('lvl3', 1)
    },
    checkCollision() {
      this.literally_the_whole_game();
      this.isJump -= 1;
      this.isStop = 0;
      if(this.isJump <0) {
        this.isJump = 0
      }
    }
  },


}

</script>
<style>

.jorge{
  display: flex;
  justify-content: space-evenly;
}

.suc{
  background-color: #04aa6d;
  color: white;
  padding: 16px 20px;
  border: none;
  cursor: pointer;
  width: 20%;
  border-radius: 50px;
  height: auto;    
  font-weight: bold;
}
.suc:hover {
  opacity: 0.5;
}

.alert-lose{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgb(158, 228, 158);
  padding: 20px;
  border: 5px solid darkgreen;
  border-radius: 20px;
  padding: 5px;
  color: green;
  font-weight: bold;
  font-size: 1em;
  width: 670px;
}

.popup-game {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1;
}
.popup-game2 {

  position:absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: pink;
  padding: 20px;
  border: 5px solid rgb(116, 3, 3);
  border-radius: 20px;
  padding: 5px;
  color: rgb(170, 14, 14);
    font-weight: bold;
    font-size: 1.5em;
}

#relogio{
  position: absolute;
  top: 0;
  left: 0;
  background-color: aliceblue;
  border-radius: 20px ;
  border-color: darkgreen;
  border: solid;
  padding: 10px;
  margin: 15px;
  color: darkgreen;
    text-shadow: 1px 1px 3px black;
    font-weight: bold;
    font-size: 2em;
}
#vida{
  position: absolute;
  margin: 15px;
  margin-top: 60px;
  top: 0;
  left: 0;
  color: darkgreen;
    text-shadow: 1px 1px 3px black;
    font-weight: bold;
    font-size: 2em;
}

.background {
  height: 50%;
  position: absolute;
  top: 0;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: end;
  background-color: black;
}

.background .elapsed {
  transition: all 1s linear;
}

/*----------- gamewindow -----------*/
.gameWindow {
  border: 5px solid green;
  border-radius: 5px;
  padding: 5px;
  width: 29.2cm;
  /* tem de estar igual ao gameGackground */
  height: 23.6cm;
  /* tem de estar igual ao gameGackground */
  display: block;
  margin: 0 auto;

  position: relative;
}

/*----------- end of gamewindow -----------*/

/*----------- gameGackground -----------*/
.gameGackground {
  /*background: url('../assets/gameScreens/proto.png') no-repeat 50% 50%;*/
  width: 29.2cm;
  /* tem de estar igual ao gameWindow */
  height: 100%;
  /* tem de estar igual ao gameWindow */
  position: absolute;
  object-fit: cover;


}

/*----------- end of gameGackground -----------*/

/*----------- Skater Avatar -----------*/
#skaterRight {
  position: absolute;
  width: 100%;
  max-width: 100px;
  height: 200px;
  padding: 0;

  margin-top: 415px;
  margin-left: 60px;
}

#skaterLeft {
  position: absolute;
  width: 100%;
  max-width: 100px;
  height: 200px;
  padding: 0;

  margin-top: 415px;
  margin-left: -160px;
  /* wow */
}

/*----------- end of Skater Avatar -----------*/

/*----------- buttons -----------*/
.buttons {
  /* Div that contains the buttons */
  display: block;
  margin: 0 auto;

  width: 400px;
  padding: 10px;

  /* I used brute force lol*/
  margin-top: 550px;
  z-index: 5;
}

#go {
  display: block;
  margin: 0 auto;
  width: 100%;
  max-width: 100px;
  height: 100px;
  position: relative;
  padding: 0;
  /*delete the button*/
  opacity: 0%;
}

#stop {
  position: relative;
  width: 100%;
  max-width: 100px;
  height: 100px;
  margin: 5px;
}

#left {
  position: relative;
  width: 100%;
  max-width: 100px;
  height: 100px;
  padding: 0;
}

#right {
  position: relative;
  width: 100%;
  max-width: 100px;
  height: 100px;
  padding: 0;
}

#jump {
  display: block;
  margin: 0 auto;
  width: 100%;
  max-width: 310px;
  height: 100px;
  position: relative;
}

.btimg {
  width: 100%;
  height: 100%;
}

.buttonsBackgroundColor {
  background-color: lightgreen;
}

.buttonsBackgroundColor:hover {
  opacity: 0.4;
}

/*----------- end of buttons -----------*/
</style>

