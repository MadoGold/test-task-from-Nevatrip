<template>
  <div class="card">
    <div class="card__img">
      <img :src="item.img" alt="image">
      <div v-if="item.mark"
           class="card__img-info"
           :style="{backgroundColor: item.mark.backColor, color: item.mark.textColor}"
      >
        {{ item.mark.text }}
      </div>
    </div>
    <div class="card__inner">
      <p class="card__travel-time card__travel-time-mobile">{{ item.travelTime }} часа</p>
      <h2 class="card__title">{{ item.title }}</h2>
      <p class="card__travel-time">{{ item.travelTime }} часа</p>
      <div class="card__info">
        <p>Билет на целый день</p>
        <p>Неограниченное число катаний</p>
        <p>6 остановок у главных достопримечательностей</p>
        <p class="card__race-time">
          <span>Ближайший рейс сегодня</span>
          <CardList :times="item.times" :className="'card__list'"/>
        </p>
      </div>
      <div class="card__footer">
        <div class="card__price">
          <p>{{ item.price }} ₽</p>
          <p v-if="item.berthPrice">{{ item.berthPrice }} ₽ на причале</p>
        </div>
        <button class="card__button">Подробнее</button>
      </div>
    </div>
  </div>
</template>

<script>
import CardList from "@/components/CardList";
export default {
  props: {
    item: {
      type: Object,
      required: true,
    }
  },
  components: { CardList }
}
</script>

<style scoped lang="scss">
.card {
  margin: 0 auto 60px;
  max-width: 1100px;
  border: 0.3px solid #828282;
  border-radius: 16px;
  overflow: hidden;

  &__img {
    position: relative;
    padding-bottom: 65%;

    img {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      object-fit: cover;
    }

    &-info {
      padding: 5px;
      position: absolute;
      top: 40px;
      left: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      min-width: 99px;
      min-height: 35px;
      background-color: #FED74B;
      font-size: 12px;
      font-weight: 600;
      color: #3E3E3E;

      @media (min-width: 767.9px) {
        min-width: 154px;
        min-height: 42px;
        font-size: 16px;
      }
    }
  }

  &__inner {
    padding: 14px 12px 18px;
  }

  &__travel-time {
    display: none;
    position: relative;
    padding-left: 25px;
    margin-bottom: 10px;
    font-size: 12px;
    color: #9E9E9E;

    &:before {
      content: '';
      position: absolute;
      height: 16px;
      width: 16px;
      top: 50%;
      left: 0;
      transform: translateY(-50%);
      background: url("../assets/clock-icon.svg") no-repeat center / contain;
    }

    &-mobile {
      display: block;
    }

    @media (min-width: 767.9px) {
      display: block;

      &-mobile {
        display: none;
      }
    }
  }

  &__title {
    margin-bottom: 16px;
    font-weight: 600;
    font-size: 14px;
    line-height: 22px;
  }

  &__info {
    padding: 0 37px;

    p {
      position: relative;

      &:not(:last-of-type) {
        margin-bottom: 10px;
      }

      &:before {
        content: '';
        position: absolute;
        top: 5px;
        left: -36px;
        width: 16px;
        height: 16px;
        background: url("../assets/check-mark.svg") no-repeat center / contain;
      }
    }
  }

  &__list {
    margin-top: 7px;
    margin-bottom: 35px;
  }

  &__footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__price {
    margin-right: 20px;

    p {
      font-size: 30px;
      line-height: 20px;
      color: #000000;

      &:not(:first-of-type) {
        font-size: 10px;
      }
    }
  }

  &__button {
    padding: 12px 41px;
    background-color: #FED74B;
    border: 0.5px solid #CBA500;
    border-radius: 20px;
    color: #404040;
    transition: all .3s ease-in-out;
    cursor: pointer;

    &:hover {
      background-color: #ffcd1e;
    }
  }
}


@media (min-width: 767.9px) {
  .card {
    display: flex;

    &__img {
      flex: 1 1 43%;
      padding-bottom: 0;
    }

    &__inner {
      padding: 14px 22px 18px;
      flex: 1 1 57%;
    }

    &__title {
      margin-bottom: 11px;
      font-size: 26px;
      line-height: 1.3;
    }

    &__footer {
      justify-content: flex-start;
    }
  }
}

@media (min-width: 950px) {
  .card {

    &__race-time {
      margin-bottom: 24px;
      display: flex;
      gap: 7px;
    }

    &__list {
      margin: 0;
    }
  }
}
</style>
