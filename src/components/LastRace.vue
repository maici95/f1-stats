<template>
    <div>
        <div class='last-race'>
            {{ lastRace }}
        </div>

        <div class='container'>
            <div
                v-for='(d, i) in top3'
                :key='i'
                class='podium'
            >
                <img
                    src='@/assets/unk.png'
                    class='driver-image'
                />
                <div
                    class='name-tag'
                    :style='{
                        background: teamColor(d.teamId)
                    }'
                >
                    {{ d.name }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import data from '../assets/data.json';
import results from '../assets/results.json';

export default {
    computed: {
        lastRace() {
            return 'Last race ' + data.races.find(e => e.id == results[results.length - 1].raceId).name;
        },

        top3() {
            return [
                data.drivers.find(e => e.id == results[results.length - 1].result[1]),
                data.drivers.find(e => e.id == results[results.length - 1].result[0]),
                data.drivers.find(e => e.id == results[results.length - 1].result[2])
            ];
        },

        teams() {
            return data.teams;
        },
    },

    methods: {
        teamColor(id) {
            return this?.teams?.find(e => e.id == id)?.color;
        },
    }
}
</script>

<style scoped>
.container {
    padding: 20px;
    display: flex;
    justify-content: center;
    height: 235px;
}
.podium {
    box-shadow: 0 0 4px #000;
}
.container > * {
    margin: 0 10px;
    background: #c9b037;
}
.container > *:first-child {
    background: #d7d7d7;
}
.container > *:last-child {
    background: #ad8a56;
}

.driver-image {
    height: 180px;
}
.name-tag {
    text-align: center;
    padding: 10px 0;
    font-weight: bold;
    font-size: 20px;
    color: #fff;
    text-shadow: 1px 1px 0 #000;
}
.last-race {
    text-align: center;
    padding: 20px 0;
    font-size: 30px;
    background: #222;
    color: #ffffff;
    text-shadow: 1px 1px 0 #000;
    border-bottom: 6px solid #555;
}
</style>
