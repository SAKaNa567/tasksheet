<template id="">
  <div class="timer">
    <div id="displaytime">
      <p id="time">
        {{ showtime }}
      </p>
    </div>
    <div id="buttons">
      <div id="start">
        <input type="button" id="start_button" v-bind:value="start_or_reset" v-on:click="startButton">
      </div>
      <div id="stop">
       <input type="button" id="pause_button" value="pause" v-on:click="pauseButton">
     </div>
    </div>

  </div>
</template>
<script>
export default {

  name: 'Timer',
  data: function () {
    return {
      converted_time: this.displayTime(0),
      startTime: 0,
      updatedTime: 0,
      savedTime:0,
      paused:1,
      differenceTime: 0,
      showtime: this.converted_time,
      interval: 0,
      start_or_reset: 'start'
    }
  },
  methods: {
    startButton: function() {
      if(this.startTime === 0){
        this.startTime = new Date().getTime();
        this.paused = 0;
        this.interval = setInterval(this.getShowTime,1000)
        // document.getElementById('start').innerHTML = "<input type='button' id='start_button' value='reset' v-on:click='startButton'>";
        this.start_or_reset = 'reset';

      } else if(this.startTime){
        // document.getElementById('start').innerHTML =  "<input type='button' id='start_button' value='start' v-on:click='startButton'>";
        this.start_or_reset = 'start';

        clearInterval(this.interval);
        this.displayTime(0);
        this.showtime = this.converted_time;
        this.startTime = 0;
        this.updatedTime = 0;
        this.savedTime = 0;
        this.paused=1;
        this.differenceTime = 0;
      }
    },
    getShowTime: function (){//okay
      this.updatedTime = new Date().getTime();
      this.differenceTime = this.updatedTime - this.startTime;
      if (this.savedTime){
        this.displayTime(this.differenceTime+this.savedTime);
        this.showtime = this.converted_time;
      } else {
        this.displayTime(this.differenceTime);
        this.showtime = this.converted_time;
      }

    },
    displayTime: function(time) {//okay
      let hours = Math.floor((time % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      let minutes = Math.floor((time % ( 1000 * 60 * 60)) / (1000 * 60));
      let seconds = Math.floor((time % ( 1000 * 60 )) / 1000);
      this.converted_time = ((hours > 0) ? hours+" hour " : "") + ((minutes > 0) ? minutes+" min " : "") + seconds + " sec";
    },
    pauseButton: function() {
      if(this.paused){
        if(this.startTime){
          this.paused = 0;
          this.startTime = new Date().getTime();
          this.interval = setInterval(this.getShowTime,1000);
        }
      }else if (this.paused === 0){
        this.savedTime = this.differenceTime+this.savedTime;
        clearInterval(this.interval);
        this.paused=1;
      }
    }
  }
}

</script>
<style media="screen">
    .timer{
      /* border: solid 10px black; */
      width: 90%;
      height: 100%;
      margin: auto;
      background: #2ca9e1;
      text-align:  center;
    }
    #displaytime{
      /* font-size: 300%; */
    }
</style>
