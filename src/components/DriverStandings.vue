<template>
    <div>
        <div
            v-for='(d, i) in driverStandings'
            :key='i'
            class='row'
            :style='{
                borderLeft: "10px solid " + d.team.color,
            }'
        >
            <div>{{ i + 1 }}</div>
            <div>{{ d.name }}</div>
            <div>{{ d.team.name }}</div>
            <div>{{ d.points }}</div>
        </div>
    </div>
</template>

<script>
import data from '../assets/data.json';
import results from '../assets/results.json';

const getPoints = result => ({
    1: 25,
    2: 18,
    3: 15,
    4: 12,
    5: 10,
    6: 8,
    7: 6,
    8: 4,
    9: 2,
    10: 1
}[result]);

export default {
    computed: {
        driverStandings() {
            let drivers = [];
            results;

            data.drivers.forEach(e => {
                const races = [];

                results.forEach(race => {
                    race.result.forEach((r2, i) => {
                        if (r2 == e.id) {
                            races.push(i + 1);
                        }
                    });
                });

                let points = 0;

                results.forEach(race => {
                    if (race.fastestLapDriverId == e.id) {
                        points++;
                    }
                });

                races.forEach(e => {
                    points += getPoints(e);
                });

                if (isNaN(points)) {
                    points = 0;
                }

                drivers.push({
                    ...e,
                    points: points,
                    team: data.teams.find(t => t.id == e.teamId)
                });
            });

            drivers.sort((a, b) => b.points - a.points);

            return drivers;
        }
    }

}
</script>

<style scoped>
.row {
    display: grid;
    grid-template-columns: 10% 40% 40% 10%;
    padding: 15px;
    border-bottom: 1px solid #ddd;
}
.row > *:last-child {
    text-align: right;
}
.row:hover {
    background: #ddd;
}
</style>
