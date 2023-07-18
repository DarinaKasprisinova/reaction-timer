<template>
  <div>
    <p>Your reaction time - {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "God Tier Fast. I salute you!";
    } else if (this.score < 350) {
      this.rank = "Rapid Reflexes!!";
    } else if (this.score < 450){
      this.rank = "You are fast, but not fastest..";
    } else if (this.score < 550) {
      this.rank = "You are slow baby";
    } else {
      this.rank = "Snail pace...";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
