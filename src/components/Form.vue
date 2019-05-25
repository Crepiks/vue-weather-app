<template>
    <form class="weather-form" @submit.prevent="getWeather">
        <input class="weather-form__input" type="text" name="city" autocomplete="off" @input="onCityChange">
        <button type="submit">Find</button>
    </form>
</template>

<script>
export default {
    name: 'weather-form',
    data() {
        return{
            
        }
    },
    methods: {
        getWeather() {
            this.$emit('get-data');
        },
        onCityChange(e) {
            let cityName = e.target.value;
            this.$emit('change-city', cityName);
        }
    }
}
</script>

<style lang="scss" scoped>

form {
    height: 40%;
    display: flex;
    justify-content: center;
    align-items: center;
}

input[type="text"] {
    background-color: transparent;
    border: 0;
    border-bottom: solid 2px #113a65;
    width: 50%;
    padding-bottom: 4px;
    color: #fff;
    font-weight: lighter;
    margin-right: 20px;
    font-size: 20px;
    outline: none;
}

input::-webkit-input-placeholder {
    color: #103a65;
}

input::-moz-placeholder {
    color: #103a65;
}

button {
    border: 2px solid #103a65;
    border-bottom: 4px solid #103a65;
    padding: 8px 20px;
    margin: 0 2px;
    border-radius: 2px;
    cursor: pointer;
    background-color: #235d9c;
    color: #fff;
    outline: none!important;
}

button:hover {
    border-bottom: 2px solid #103a65;
    position: relative;
    top: 2px;
}

button:active {
    border-bottom: 2px solid transparent;
    border-color: transparent;
    position: relative;
    top: 2px;
}
</style>