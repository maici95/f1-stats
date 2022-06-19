<template>
    <div>
        <race-result
            v-if='1 == 2'
        />
        <driver-standings
        
        />
    </div>
</template>

<script>
import DriverStandings from './components/DriverStandings.vue'
import RaceResult from './components/RaceResult.vue'

export default {
	components: { RaceResult, DriverStandings },

}
</script>

<style>
* {
    padding: 0;
    margin: 0;
    font-size: 18px;
    font-family: Arial;
}

select {
    font-size: 18px;
    height: 60px;
    padding: 0 10px;
}
option {
    zoom: 1.5;
}
button {
    padding: 20px;
}
</style>
