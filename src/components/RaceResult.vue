<template>
    <div
        class='form'
    >
        <select
            v-model='raceId'
        >
            <option
                v-for='(r, i) in races'
                :key='i'
                :label='r.name'
                :value='r.id'
            />
        </select>

        <select
            v-model='fastestLapDriverId'
            class='fastest-lap'
        >
            <option
                v-for='(d, i) in driverList'
                :key='i'
                :label='d.name'
                :value='d.id'
                :style='{background: teamColor(d.teamId)+"C8", color: "#000"}'
            />
        </select>

        <div
            v-for='(r, i) in result'
            :key='i'
            class='row'
        >
            <div
                class='row-number'
            >
                {{ i + 1}}
            </div>
            <select
                v-model='result[i]'
            >
                <option
                    v-for='(d, i2) in driverOptions'
                    :key='i2'
                    :label='d.name'
                    :value='d.id'
                    :hidden='result.includes(d.id)'
                    :style='{background: teamColor(d.teamId)+"C8"}'
                />
            </select>
        </div>

        <button
            @click='copyRaceJson'
        >
            Get Race JSON
        </button>

        <div>
            {{ json }}
        </div>
    </div>
</template>

<script>
import data from '../assets/data.json';

export default {
    data() {
        return {
            result: Array(10).fill(-1),
            raceId: -1,
            fastestLapDriverId: -1,
            json: ''
        }
    },

    computed: {
        driverList() {
            return data.drivers;
        },

        driverOptions() {
            return data.drivers;
        },

        teams() {
            return data.teams;
        },

        races() {
            return data.races;
        }
    },

    methods: {
        teamColor(id) {
            return this?.teams?.find(e => e.id == id)?.color;
        },

        copyRaceJson() {
/*             if (this.raceId == -1) return alert('invalid race result');
            if (this.fastestLapDriverId == -1) return alert('invalid race result');
            if (!this.result.every(e => e != -1)) return alert('invalid race result');
 */
            const obj = {
                raceId: this.raceId,
                fastestLapDriverId: this.fastestLapDriverId,
                result: this.result
            }

            const json = JSON.stringify(obj);
            navigator.clipboard.writeText(json);

            this.json = json;
        }
    }

}
</script>

<style scoped>
.form {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin-left: calc(50% - 200px);
    margin-top: 50px;
}
.form > * {
    margin-bottom: 20px;
}
.row-number {
    width: 50px;
    border: 1px solid #555;
    border-right: 0;
    text-align: center;
}
.row {
    line-height: 50px;
    display: flex;
}
.row select {
    width: 350px;
    padding: 0 10px;
}
.fastest-lap {
    background: purple;
    color: white;
}
</style>
