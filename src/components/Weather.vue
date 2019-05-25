<template>
    <div class="weather-info">
        <h2>Weather state: {{ weatherDescription }}</h2>
        <p>Temperature: {{ temp }}</p>
    </div>
</template>

<script>
export default {
    name: 'weather-info',
    props: ['weather-description', 'temp'],
    data() {
        return {
           
        }
    }
}
</script>

<style lang="scss" scoped>

.weather-info {
    margin: auto;
    width: 80%;
}

h2 {
    font-size: 25px;
    color: #fff;
}

p {
    color: #e4e4e4;
    font-weight: bold;
}


</style>