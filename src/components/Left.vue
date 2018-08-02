<template>
  <section class="left">
    <h1>FRONT-END<br>SKILL TREE</h1>
    <div class="current">
      <div class="tag">CURRENT RANK</div>
      <h2>
        <span>FRONT-END</span>
        <br>
        <span>{{ rank[nowLevel] }}</span>
      </h2>
    </div>
    <div class="ship">
        <img :src="ship[nowLevel]" alt="img-ship-beginner">
    </div>
    <svg viewBox="0 0 200 200">
      <defs>
        <linearGradient id="orange_red" x1="0%" y1="0%" x2="0%" y2="100%" gradientTransform="rotate(45)">
        <stop offset="0%" style="stop-color:#0e0024;
        stop-opacity:1"/>
        <stop offset="70%" style="stop-color:#2d1b59;
        stop-opacity:1"/>
        </linearGradient>
      </defs>
      <polyline points="100,0 50,10 60,15 30,25 0,25 0,130 200,130 200,25 75,25 85,15 75,12 100,0" style="fill:url(#orange_red)"></polyline>
    </svg>
    <div class="welcome">
      Welcome aboard. Your mission is:
      <span>Collect the resources and learn the skills to upgrade the ship.</span>
      <br>
      Good luck, captain!
    </div>
  </section>
</template>

<script>
export default {
  name: 'Left',
  props: ['nowLevel'],
  data() {
    return {
      rank: ["NOOB", "BEGINEER", "BEGINEER", "DEVELOPER", "MASTER"],
      ship: [
        "./static/images/img-ship-noob.png",
        "./static/images/img-ship-beginner.png",
        "./static/images/img-ship-beginner.png",
        "./static/images/img-ship-developer.png",
        "./static/images/img-ship-master.png"
      ],
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss'>
@import '../style/components/left.scss';
</style>
