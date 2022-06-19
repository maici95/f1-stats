<template>
    <div>
        <race-result
            v-if='1 == 2'
        />
        <season-header
        
        />
        <last-race
        
        />
        <driver-standings
        
        />
    </div>
</template>

<script>
import DriverStandings from './components/DriverStandings.vue'
import LastRace from './components/LastRace.vue'
import RaceResult from './components/RaceResult.vue'
import SeasonHeader from './components/SeasonHeader.vue'

export default {
	components: { RaceResult, DriverStandings, SeasonHeader, LastRace },

}
</script>

<style>
* {
    padding: 0;
    margin: 0;
    font-family: Arial;
}
body {
    background: #F3F3F3;
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
