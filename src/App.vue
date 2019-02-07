<template>
    <div id="app">
        <div class="calculator">
            <div class="enterSpeed">
                <input
                        type="number"
                        class="speed"
                        @keyup="calculateKm"
                        @focus="$event.target.select()"
                        v-model="speedMiles"
                />
                miles
            </div>
            <div>Result: <b>{{ speedKilometers }}km</b></div>
            <div>
                <h4>Convert:</h4>
                <button @click="calculate">Convert Now</button>
                <div>
                    <div class="speed">
                        <p>
                            {{ meters }} meters
                        </p>
                        <p>
                            {{ feet }} feet
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
	export default {
		name: "app",
		data() {
			return {
				speedMiles: 0,
				speedKilometers: 0,
				meters: 0,
                feet: 0
			};
		},
		methods: {
			calculateMeters() {
				this.meters = Math.round(this.speedKilometers * 1000);
            },
            calculateFeet() {
                this.feet = Math.round(this.speedMiles * 5280);
            },
			calculateKm() {
				this.speedKilometers = (this.speedMiles * 1.60934).toFixed(2);
            },
            calculate() {
                this.calculateMeters();
                this.calculateFeet();
            }
		}
	};
</script>

<style>
    body {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        background: #f5f5f5;
    }
    div {
        padding: 10px 0;
    }
    .calculator {
        width: 300px;
        margin: 20px auto;
        padding: 35px;
        background-color: #fff;
    }
    input.speed {
        width: 5em;
    }
</style>
