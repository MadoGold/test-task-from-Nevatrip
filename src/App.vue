<template>
  <div v-for="item in items">
    <Card :item="item" :key="item.id" />
  </div>
</template>

<script>
import Card from '@/components/Card'

export default {
  name: 'App',
  components: {
    Card
  },
  data() {
    return {
      items: [
        {
          id: 0,
          img: '/images/card-img-2.jpg',
          title: 'Обзорная экскурсия по рекам и каналам с остановками Hop on Hop Off 2020',
          price: 900,
          times: ['12:00', '12:00', '12:00'],
          travelTime: 2,
          mark: {
            backColor: '#099CE8',
            textColor: '#FFFFFF',
            text: 'НОВИНКА',
          }
        },
        {
          id: 1,
          img: '/images/card-img-3.jpg',
          title: 'Обзорная экскурсия по рекам и каналам с остановками Hop on Hop Off 2020',
          price: 900,
          berthPrice: 1200,
          times: ['12:00', '12:00', '12:00', '12:00'],
          travelTime: 2,
          mark: {
            backColor: '#FFD83B',
            textColor: '#323232',
            text: 'КРУГЛЫЙ ГОД',
          }
        },
        {
          id: 2,
          img: '/images/card-img-4.jpg',
          title: 'Обзорная экскурсия по рекам и каналам с остановками Hop on Hop Off 2020',
          price: 900,
          berthPrice: 1200,
          times: ['12:00', '12:00', '12:00', '12:00', '12:00', '12:00', '12:00', '12:00', '12:00', '12:00', '12:00', '12:00'],
          travelTime: 2,
          mark: false
        },
        {
          id: 3,
          img: '/images/card-img-1.jpg',
          title: 'АКЦИЯ - Обзорная экскурсия по рекам и каналам  с остановками Hop on Hop Off 2019',
          price: 2900,
          berthPrice: 1200,
          times: ['12:00', '12:00', '12:00', '12:00'],
          travelTime: 2,
          mark: {
            backColor: '#FED74B',
            textColor: '#323232',
            text: 'НОВИНКА',
          }
        },
      ]
    }
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-decoration: none;
  list-style: none;
  color: inherit;
  font-family: inherit;
  border: none;
}

html,
body {
  font-family: 'Open Sans', Arial, sans-serif;
  font-size: 14px;
  line-height: 20px;
  background-color: #E5E5E5;
  color: #4B4B4B;
  min-width: 375px;
}

#app {
  padding: 26px 17px;
}
</style>
