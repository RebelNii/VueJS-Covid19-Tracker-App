<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!--grid 1-->
    <div class="shadow-md bg-blue-200 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
      <div class="text-2xl mb-4">
        <span class="font-semibold"> New:</span>
        {{ statsFormat(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-semibold"> Total:</span>
        {{ statsFormat(stats.TotalConfirmed) }}
      </div>
    </div>
    <!--grid 2-->
    <div class="shadow-md bg-red-200 hover:bg-red-500 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
      <div class="text-2xl mb-4">
        <span class="font-semibold"> New:</span>
        {{ statsFormat(stats.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-semibold"> Total:</span>
        {{ statsFormat(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script>
    export default{
        name: 'dataBoxes',
        props:['stats'],
        methods:{
            statsFormat(x){
                return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            }
        }
    }
</script>

<style>
</style>