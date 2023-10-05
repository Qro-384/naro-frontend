<script setup lang="ts">
import { ref, onMounted } from 'vue'
const props = defineProps<{ countryName: string }>()
interface City {
    Name:string;
}

const cityList = ref<City[]>([])
onMounted(async () => {
  const res = await fetch('/api/country/' + props.countryName)
  if (res.ok) {
        const data = await res.json()
        for (var i=0; i<data.length; i++){
            cityList.value.push({Name: data[i].name})
        }
    }
    if (!res.ok){
        console.error(res.toString())
    }
})
</script>

<template>
  <div>
    <h1>
      {{ countryName }}
    </h1>

  </div> 
    <ul>
        <li v-for="city in cityList" :key="city.Name">
            <td><router-link :to="{name: 'city', params:{ cityName: city.Name }}">{{ city.Name }}</router-link></td>
        </li>
    </ul>
</template>