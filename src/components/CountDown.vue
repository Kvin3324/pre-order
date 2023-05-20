<template>
  <section class="countdown">
    <div>
      <h2 v-text="title" />
    </div>
    <div id="plug">
      <p class="timer"> {{ timerOutput }} </p>
    </div>
  </section>
</template>

<script>
export default {
  name: "CountDown",
  props: {
    title: {
      type: String,
      default: ''
    }
  },

  data() {
    return {
      countDownToTime : new Date("July 29, 2023 00:00:00").getTime(),
      timerOutput:  null
    }
  },

  mounted() {
    setInterval(() => { this.startTimer() }, 50);
  },

  methods: {
    startTimer: function() {
      const timeNow = new Date().getTime();
      const timeDifference = this.countDownToTime - timeNow;
      const millisecondsInOneSecond = 1000;
      const millisecondsInOneMinute = millisecondsInOneSecond * 60;
      const millisecondsInOneHour = millisecondsInOneMinute * 60;
      const millisecondsInOneDay = millisecondsInOneHour * 24;
      const differenceInDays = timeDifference / millisecondsInOneDay;
      const remainderDifferenceInHours = (timeDifference % millisecondsInOneDay) / millisecondsInOneHour;
      const remainderDifferenceInMinutes = (timeDifference % millisecondsInOneHour) / millisecondsInOneMinute;
      const remainderDifferenceInSeconds = (timeDifference % millisecondsInOneMinute) / millisecondsInOneSecond;
      const remainingDays = Math.floor(differenceInDays);
      const remainingHours = Math.floor(remainderDifferenceInHours);
      const remainingMinutes = Math.floor(remainderDifferenceInMinutes);
      const remainingSeconds =Math.floor(remainderDifferenceInSeconds);
      this.timerOutput = remainingDays + " Jours " + ": " + remainingHours + " Heures " + ": " + remainingMinutes + " Minutes " + ": " + remainingSeconds + " Secondes";
    }
  },
}
</script>

<style>
.countdown {
  margin: 25px 0;
}

.timer {
  background-color: black;
  border-radius: 15px;
  color: white;
  font-size: .95em;
  font-weight: bold;
  margin: 40px 0;
  padding: 40px 15px;
}
</style>