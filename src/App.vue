<template>
    <div>

        <race-result />

    </div>
</template>

<script>
import RaceResult from './components/RaceResult.vue'

export default {
	components: { RaceResult },

}
</script>

<style>
* {
    padding: 0;
    margin: 0;
    font-size: 18px;
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
