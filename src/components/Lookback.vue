<template>
  <div :class="[$style.lookback, $style[$mq]]">
    <GridLayout :itemWidth="computedWidth">
      <div
        :class="$style.stat"
        v-for="(stat, i) in this.stats"
        :key="i"
        :slot="`item${i}`"
      >
        <div :class="$style.clip">
          <img :src="stat.image" :class="$style.img" />
        </div>
        <div :class="$style.name">{{ stat.name }}</div>
        <div :class="$style.value">{{ stat.value }}</div>
      </div>
    </GridLayout>
  </div>
</template>
<script>
const GridLayout = () => import("./layouts/GridLayout");

export default {
  props: {
    stats: {
      type: Array,
    },
  },
  components: {
    GridLayout,
  },
  computed: {
    computedWidth() {
      if (this.$mq == "lg") return "160px";
      return "220px";
    },
  },
};
</script>

<style module lang="stylus">
.lookback {

  .stat {
    width: 220px;

    &:nth-child(odd) {
      &::before {
        content: '';
        width: 100px;
      }
    }

    .clip {
      width: 220px;
      margin-bottom: 25px;
    }

    .img {
      width: 90%;
      position: relative;
    }

    .name, .value {
      font-family: 'Quicksand';
      font-weight: 700;
      margin-left: 50px;
      text-align: center;
      color: var(--primary-new);
      line-height: 28px;
      $font-size: 25px;
    }
  }
}
</style>
