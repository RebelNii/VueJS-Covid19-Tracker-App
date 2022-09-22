<template>
    <select @change="onChange()"
    v-model="selected" name="countries" id="countries" 
    class="form-select mt-10 w-full border border-solid rounded p-2 mb-10 bg-neutral-400 text-white">
        
        <option v-for="country in countries" :key="country.ID" :value="country.ID">
            {{country.Country}}
        </option>
    </select>
</template>

<script>
    export default{
        name: 'countryData',
        props: ['countries'],
        data(){
            return {
                selected: 0
            }
        },
        methods: {
            onChange(){
                const country = this.countries.find((item) => item.ID === this.selected)
                //console.log(country)

                this.$emit('get-country-data',country)
            }
        }
    }
</script>