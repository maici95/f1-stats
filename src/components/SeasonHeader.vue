<template>
    <div class='header'>
        <h1>
            F1 Season 2021
        </h1>
        <h2>
            {{ raceText }}
        </h2>
    </div>
</template>

<script>
import data from '../assets/data.json';
import results from '../assets/results.json';

export default {
    computed: {
        raceText() {
            return 'Races ' + results.length + '/ ' + data.season.races;
        }
    }
}
</script>


<style scoped>
.header {
    border-bottom: 1px solid #ddd;
    background-image: url('~@/assets/Header.png');
    height: 200px;
    line-height: 200px;
    background-position: center;
    border-bottom: 4px solid #FF1801;
    color: #ffffff;
    padding: 0 40px;
    font-size: 14px;
    text-shadow: 2px 2px 0 #000;
    display: flex;
    justify-content: space-between;
}
</style>