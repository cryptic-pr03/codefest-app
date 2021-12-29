<template>
  <div :class="$style.sectionContainer">
    <h1 :class="[$style.sectionTitle, $style[$mq], tooLong]">{{ title }}</h1>
    <hr :class="[$style.sectionLine, $style.line1] " />
    <hr :class="[$style.sectionLine, $style.line2]" />
    <div :style="contentStyle">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      required: true,
      type: String,
    },
    contentStyle: {
      required: false,
      type: Object,
    },
  },
  computed: {
    tooLong() {
      const title = this.$props.title;
      if (title.length > 10) {
        return this.$style.tooLong;
      }
    },
  },
};
</script>

<style module lang="stylus">
div.sectionContainer {
  margin: 36px 0;

  h1.sectionTitle {
    font-family: 'Baloo Bhaina 2';
    color: var(--heading-color);
    letter-spacing: 2px;
    $font-size: 64px;
    margin-top: 144px;
    margin-bottom: 0px;
    line-height : 1.2;

    &.lg, &.xl, &.xxl {
      padding-top: 36px;
    }

    &.xs, &.sm, &.md {
      margin-top: 72px;
    }

    &.xs {
      $font-size: 52px;
    }

    ~/:nth-child(even) h1.sectionTitle {
      text-align: start;
    }

    ~/:nth-child(odd) h1.sectionTitle {
      text-align: end;
    }
  }

  h1.tooLong {
    &.xs {
      $font-size: 36px;
    }
  }

  hr.sectionLine {
    display: block;
    border: none;
    margin: 0px 0 10px;
  }

  hr.line1{
    background-color: $vermilion;
    height: 5px;
    width: 60%;
    ~/:nth-child(even) hr.line1 {
      margin-right: 40%;
    }

    ~/:nth-child(odd) hr.line1 {
      margin-left: 40%;
    }

  }

    hr.line2{
    background-color: $vermilion;
    margin-bottom:40px;
    height: 3px;
    width: 40%;
    ~/:nth-child(even) hr.line2 {
      margin-right: 60%;
    }
    ~/:nth-child(odd) hr.line2 {
      margin-left: 60%;
    }

  }

}
</style>
