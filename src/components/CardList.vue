<template>
  <ul :class="className" class="list">
    <li
      v-for="(time, index) in timesPreview"
      class="list__item"
    >
      <span :key="index">{{ time }}</span>
    </li>
    <li
      @click="open = true"
      v-if="timesRemaining.length > 0 && open === false"
      class="list__item"
    >
      <span>ещё...</span>
    </li>
    <li
      v-if="open === true" v-for="(time, index) in timesRemaining"
      class="list__item"
    >
      <span :key="index">{{ time }}</span>
    </li>
    <li
      @click="open = false"
      v-if="timesRemaining.length > 0 && open === true"
      class="list__item"
    >
      <span>скрыть</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    times: {
      type: Array,
      required: true,
    },
    className: {
      type: String,
      required: false,
    }
  },
  data() {
    return {
      open: false,
    }
  },
  computed: {
    timesPreview() {
      return this.times.slice(0, 3);
    },
    timesRemaining() {
      return this.times.slice(3);
    },
  }
}
</script>

<style scoped lang="scss">
.list {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  flex-shrink: 2;
  gap: 7px;

  &__item {
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 64px;
    height: 24px;
    background-color: #D9E8FF;
    border-radius: 11px;
    cursor: pointer;
    transition: all .1s ease-in-out;

    span {
      color: #343434;
    }

    &:hover {
      background: #6BA6FF;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.25);

      span {
        color: #fff;
      }
    }
  }
}
</style>
