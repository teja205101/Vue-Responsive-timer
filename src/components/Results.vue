<template>
  <h1>Reaction Time: {{ time }} Sec</h1>
  <h2>{{ rank }}</h2>
</template>
<script>
export default {
  name: "ResultsOfTime",
  props: ["time"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.time < 3) {
      this.rank = "Good Reaction Time";
    } else if (3 < this.time && this.time < 6) {
      this.rank = "Avg. Reaction Time";
    } else {
      this.rank = "Too Slow ...";
    }
  },
};
</script>
