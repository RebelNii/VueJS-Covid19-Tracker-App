<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="stats" />
    <Country @get-country-data="getCountryData" :countries="countries" />
    <button v-if="stats.Country" @click="resetData"
    class="bg-yellow-600 p-2 text-base mb-10 border-none outline-none rounded hover:bg-yellow-300">
      Reset
    </button>
  </main>

  <main class="flex flex-col justify-center text-center p-4" v-else>
    <div class="text-gray-500 mt-10 mb-6 text-3xl">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-24 m-auto" alt="">
  </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from '../components/dataTitle.vue'
import DataBoxes from '@/components/DataBoxes'
import Country from '@/components/CountryData'


export default {
  name: 'HomeView',
  components: {
    DataTitle,
    DataBoxes,
    Country
},
  data(){
    return{
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries:[],
      loadingImage: require('../assets/gif/updatess.gif')
    }
  },
  methods:{
    async fetchCovidData(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      this.dataDate = data.Date//assign dataDate date we fetch from api
      this.stats = data.Global;//get global stats and assign to stats
      this.countries = data.Countries;
      this.loading = false;
      console.log(data);
      return data;
    },

    getCountryData(country){
        this.stats = country;
        this.title = country.Country
    },

    async resetData(){
      this.loading = true

      const datas = await this.fetchCovidData();
      this.title = 'Global'
      this.stats = datas.Global;//get global stats and assign to stats
      this.loading = false

    }
  },
  created(){
    this.fetchCovidData()
  }
}
</script>
