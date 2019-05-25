<template>
    <div class="weather-picture">

    </div>
</template>

<script>
export default {
    name: "weather-picture"
}
</script>

<style lang="scss">
.weather-picture {
    background: url("../assets/forest.jpg") center center no-repeat;
    background-blend-mode: multiply;
    background-color: #484747;
    border: 2px solid #1f1f1f;
    border-right: 2px solid #131e29;
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: #000;
}
</style>

