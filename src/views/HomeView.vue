<template>

  <div class="category p-4 my-2 lg:px-16" v-if="data !== null">

    <div class="flex space-x-16 mb-4 items-center">
      <h1 class="text-2xl font-bold">Акции</h1>
      <img src="../assets/arrow-right.svg" alt="" width="40">
    </div>

    <div class="flex items-stretch space-x-4 overflow-x-auto slider" style="scroll-snap-type: x mandatory;">

      <div class="card border-2 p-4 rounded-lg hover:shadow-xl flex flex-col justify-between" v-for="(book,index) in data.sales"
      :key="index" style="max-width: 170px;" @click="navigate('/book/' + book.id)">
        <div>
          <img :src="book.cover" alt="" height="280" width="150">
          <h3 class="text-start text-md mt-4 mb-2 text-grey-500 line-through">{{ book.prev_price }}</h3>

          <div class="flex items-center justify-between">
            <h2 class="text-start text-2xl mb-2 text-red-500">{{ book.cur_price }}</h2>
            <div class="px-2 bg-red-700 rounded-full">
              <h4 class="text-lg text-white font-semibold">{{ book.sales_per }} %</h4>
            </div>
          </div>

          <h1 class="text-start text-sm font-semibold break-words" style="max-width: 120px;">{{ book.name }}</h1>
          <h2 class="text-start text-sm font-light mb-4" style="max-width: 120px;">{{ book.author }}</h2>

          
        </div>

        <div>
          <div class="flex items-center mb-4" style="margin-top: auto">
              <img src="../assets/star_active.png" alt="" width="25" v-for="star in book.stars"> 
          </div>
          <div class="flex items-stretch justify-between space-x-2">
            <button style="background: #26a9e0;flex: 1;" class="px-4 rounded-lg font-bold text-lg text-white" @click="addToCart(book.id)">Купить</button>
            <img src="../assets/bookmark-2.svg" alt="" width="45" class="p-2 rounded-xl" 
            style="background: #ecf6fe;">
          </div>
        </div>
      </div>






    </div>

  </div>







  <div class="category p-4 my-2 lg:px-16" v-if="data !== null">

    <div class="flex space-x-16 mb-4 items-center">
      <h1 class="text-2xl font-bold">Новые</h1>
      <img src="../assets/arrow-right.svg" alt="" width="40">
    </div>

    <div class="flex items-stretch space-x-4 overflow-x-auto slider" style="scroll-snap-type: x mandatory;">

      <div class="card border-2 p-4 rounded-lg hover:shadow-xl flex flex-col justify-between" v-for="(book,index) in data.newBooks"
      :key="index" style="max-width: 170px;" @click="navigate('/book/' + book.id)">
        <div>
          <img :src="book.cover" alt="" height="280" width="150">

          <div class="flex items-center justify-between mt-4">
            <h2 class="text-start text-2xl mb-2 text-red-500">{{ book.cur_price }}</h2>
            
          </div>

          <h1 class="text-start text-sm font-semibold break-words" style="max-width: 120px;">{{ book.name }}</h1>
          <h2 class="text-start text-sm font-light mb-4" style="max-width: 120px;">{{ book.author }}</h2>

          
        </div>

        <div>
          <div class="flex items-center mb-4" style="margin-top: auto">
              <img src="../assets/star_active.png" alt="" width="25" v-for="star in book.stars"> 
          </div>
          <div class="flex items-stretch justify-between space-x-2">
            <button style="background: #26a9e0;flex: 1;" class="px-4 rounded-lg font-bold text-lg text-white" @click="addToCart(book.id)">Купить</button>
            <img src="../assets/bookmark-2.svg" alt="" width="45" class="p-2 rounded-xl" 
            style="background: #ecf6fe;">
          </div>
        </div>
      </div>
    </div>

  </div>




  <div class="category p-4 my-2 lg:px-16" v-if="data !== null">

    <div class="flex space-x-16 mb-4 items-center">
      <h1 class="text-2xl font-bold">Топ продажи</h1>
      <img src="../assets/arrow-right.svg" alt="" width="40">
    </div>

    <div class="flex items-stretch space-x-4 overflow-x-auto slider" style="scroll-snap-type: x mandatory;">

      <div class="card border-2 p-4 rounded-lg hover:shadow-xl flex flex-col justify-between" v-for="(book,index) in data.topSelling"
      :key="index" style="max-width: 170px;" @click="navigate('/book/' + book.id)">
        <div>
          <img :src="book.cover" alt="" height="280" width="150">

          <div class="flex items-center justify-between">
            <h2 class="text-start text-2xl mb-2 text-red-500 mt-4">{{ book.cur_price }}</h2>
          </div>

          <h1 class="text-start text-sm font-semibold break-words" style="max-width: 120px;">{{ book.name }}</h1>
          <h2 class="text-start text-sm font-light mb-4" style="max-width: 120px;">{{ book.author }}</h2>

          
        </div>

        <div>
          <div class="flex items-center mb-4" style="margin-top: auto">
              <img src="../assets/star_active.png" alt="" width="25" v-for="star in book.stars"> 
          </div>
          <div class="flex items-stretch justify-between space-x-2">
            <button style="background: #26a9e0;flex: 1;" class="px-4 rounded-lg font-bold text-lg text-white" @click="addToCart(book.id)">Купить</button>
            <img src="../assets/bookmark-2.svg" alt="" width="45" class="p-2 rounded-xl" 
            style="background: #ecf6fe;">
          </div>
        </div>

      </div>
    </div>


  </div>



  <BottomBar/>













</template>


<script>
//© 2023, Читай-город @ is an alias to /src
import '../assets/tailwind.css'
import axios from 'axios'
import BottomBar from '../components/BottomBar.vue'


export default {
  name: 'HomeView',
  components: {
    BottomBar
  },
  data: () => ({
    books: null,
    booksBeforeProduction: [
      {id: 56784,cover: 'https://assets.asaxiy.uz/product/items/desktop/1fa8cad73d1f7d6bbfa2dc48c7170ded2022070122064656859KiUwSU0Df5.jpg.webp',prev_price: '100 c.', cur_price: '80 c.', sales_per: '20 %',stars: [1,1,1], name: 'Как завоевывать друзей и оказывать влияние...',author: 'Дейл Карнеги' 
      },
      {id: 56784,cover: 'data:image/jpeg;base64,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', prev_price: '150 c.', cur_price: '99 c.', sales_per: '33 %',stars: [1,1,1,1,1], name: '7 Навыков высокоэффективных людей',author: 'Стивен Кови'},
      {id: 56784,cover: 'data:image/jpeg;base64,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', prev_price: '160 c.',cur_price: '80 c.', sales_per: '50 %',stars: [1,1,1,1], name: 'Думай и богатей',author: 'Наполеон Хилл'}
    ],
    newBooks: [
    {id: 56784,cover: 'https://img4.labirint.ru/rc/22a477e02aef4f5ce3cc6497e8d51169/363x561q80/books59/585230/cover.jpg?1613813103',prev_price: '75 c.', cur_price: '45 c.', sales_per: '37 %',stars: [1,1,1,1], name: '1984',author: 'Джордж Оруэлл' 
      },
    ],
    data: null,
  }),
  methods: {
    navigate(To) {
      this.$router.push(To)
    },
    addToCart(id) {
      this.$store.state.cartBooks.push(id)
      // this.$store.state.newInCart += 1

      console.log(this.$store.state.cartBooks)
    }
  },
  async mounted() {
    await axios.get(`${process.env.VUE_APP_API_URL}/getMainData/`)
      .then(data => {
        console.log(data)
        this.data = data.data
        console.log(this.data)
      })
      .catch(e => {
        console.log(e)
      })
      console.log(process.env.VUE_APP_NAME)
  }
}
</script>


<style>
  .slider > div {
    scroll-snap-align: start;
  }
  .slider::-webkit-scrollbar {
    display: none;
  }
</style>