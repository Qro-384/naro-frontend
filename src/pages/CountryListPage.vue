<script setup lang="ts">
import {ref, onMounted} from 'vue'
interface Country {
    Name:string;
}
const countryList = ref<Country[]> ([])
onMounted(async () => {
    const res = await fetch('/api/countries')
    if (res.ok) {
        var data = await res.json()
        for (var i=0; i<data.length; i++){
            countryList.value.push({Name: data[i].name})
        }
    }
    if (!res.ok){
        console.error(res.toString())
    }
})

</script>

<template>
    <div>CountryList</div>
    <ul>
        <li v-for="country in countryList" :key="country.Name">
            <td><router-link :to="{name: 'country', params:{ countryName: country.Name }}">{{ country.Name }}</router-link></td>
        </li>
    </ul>
</template>