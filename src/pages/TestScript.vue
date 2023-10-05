<script setup lang='ts'>
const json = '[{"A": "a"}, {"B": "b"}, {"C": "c"}]'
const data = JSON.parse(json)
</script>
<template>
    <div>{{ data[0].A }}</div>
</template>