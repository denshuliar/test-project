<template>
  <div class="HomeBusinessCharts__wrapper">
    <div
        class="HomeBusinessCharts__item"
        v-for="stat in data"
        :key="stat.id"
    >
      <span>{{stat.value}}</span>

      <div class="HomeBusinessCharts__value"></div>
    </div>
  </div>
</template>

<script lang="js">
export default {
  name: 'HomeBusinessCharts',

  props: {
    data: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style lang="scss" scoped>
  .HomeBusinessCharts {
    &__wrapper {
      display: grid;
      grid-column-gap: 1px;
      grid-template-columns: repeat(14, 1fr);
      align-items: end;
      height: 100%;
      min-height: 758px;
      margin-top: -10%;
    }

    &__item {
      height: 100%;
      display: flex;
      flex-wrap: wrap;
      flex-direction: column;
      align-items: center;
      justify-content: flex-end;
      position: relative;

      span {
        color: $red;
        font-size: 15px;
        position: absolute;
        left: 50%;
        bottom: 100%;
        transform: translateX(-50%);
      }
    }

    &__value {
      background-color: $red;
      height: 100%;
      width: 100%;
    }
  }
</style>