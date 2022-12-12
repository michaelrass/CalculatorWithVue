<template>
	<section class="converter">
		<button @click="toggleMenuVisible" class="button__converter-menu">Converter Menu</button>

		<div v-if="menuVisible" class="converter__menu-list">
			<button @click="toggleMenuItem1" class="menu-list__items">Length</button>
			
			<div v-if="menuItem1Visible" class="item-1__content">
				<div class="content__container">
					<input class="content__input-1" @input="calculateInputMM" v-model="mmValue" type="number" name="" id="millimeter"><label for="millimeters"> Millimeters</label>
				</div>
				
				<div class="content__container">
					<input class="content__input-2" @input="calculateInputCM" v-model="cmValue" type="number" name="" id="centimeters"><label for="centimeters"> Centimeters</label>
				</div>
				
				<div class="content__container">
					<input class="content__input-3" @input="calculateInputM" v-model="mValue" type="number" name="" id="meters"><label for="meters"> Meters</label>
				</div>
				
				<div class="content__container">
					<input class="content__input-4" @input="calculateInputKM" v-model="kmValue" type="number" name="" id="kilometers"><label for="kilometers"> Kilometers</label>
				</div>
			</div>
			
			<button @click="toggleMenuItem2" class="menu-list__items">CelsiusToFahrenheit</button>
			
			<div v-if="menuItem2Visible" class="item-2__content">
				<input @input="calculateInputCelsius" v-model="celsiusValue" 
				class="input__celsius" 
				type="number" 
				name="celsiusinput" 
				id="celsius" 
				placeholder="Celsius">

				<span> = </span>

				<input @input="calculateInputFahrenheit" v-model="fahrenheitValue"
				class="input__fahrenheit"
				type="number"
				name="fahrenheitinput"
				id="fahrenheit"
				placeholder="Fahrenheit">
			</div>
			
			<button @click="toggleMenuItem3" class="menu-list__items">Weight</button>
			
			<div v-if="menuItem3Visible" class="item-1__content">
				<div class="content__container">
					<input v-model="gramsValue" @input="calculateInputGrams" class="content__input-1" type="number" name="" id="grams"><label for="grams"> Grams</label>
				</div>
				
				<div class="content__container">
					<input v-model="hektogramsValue" @input="calculateInputHektograms" class="content__input-2" type="number" name="" id="hektograms"><label for="hektograms"> Hektograms</label>
				</div>
				
				<div class="content__container">
					<input v-model="kilogramsValue" @input="calculateInputKilograms" class="content__input-3" type="number" name="" id="kilograms"><label for="kilograms"> Kilograms</label>
				</div>
				
				<div class="content__container">
					<input v-model="tonnesValue" @input="calculateInputTonnes" class="content__input-4" type="number" name="" id="tonnes"><label for="tonnes"> Tonnes</label>
				</div>
			</div>

			<button @click="toggleMenuItem4" class="menu-list__items">Time</button>
			
			<div v-if="menuItem4Visible" class="item-1__content">
				<div class="content__container">
					<input v-model="secondsValue" @input="calculateInputSeconds" class="content__input-1" type="number" name="" id="seconds"><label for="seconds"> Seconds</label>
				</div>
				
				<div class="content__container">
					<input v-model="minutesValue" @input="calculateInputMinutes" class="content__input-2" type="number" name="" id="minutes"><label for="minutes"> Minutes</label>
				</div>
				
				<div class="content__container">
					<input v-model="hoursValue" @input="calculateInputHours" class="content__input-3" type="number" name="" id="hours"><label for="hours"> Hours</label>
				</div>
				
				<div class="content__container">
					<input v-model="daysValue" @input="calculateInputDays" class="content__input-4" type="number" name="" id="days"><label for="days"> Days</label>
				</div>

			</div>	
		</div>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				maxLength: 5,
				menuVisible: false,
				menuItem1Visible: false,
				menuItem2Visible: false,
				menuItem3Visible: false,
				menuItem4Visible: false,
				mmValue: '',
				cmValue: '',
				mValue: '',
				kmValue: '',
				celsiusValue: '',
				fahrenheitValue: '',
				gramsValue: '',
				hektogramsValue: '',
				kilogramsValue: '',
				tonnesValue: '',
				secondsValue: '',
				minutesValue: '',
				hoursValue: '',
				daysValue: '',
				error: 'ERROR',
			}
		},

		computed: {
			mmValueAsNumber() {
				return Number(this.mmValue);
			},

			cmValueAsNumber() {
				return Number(this.cmValue);
			},

			mValueAsNumber() {
				return Number(this.mValue);
			},

			kmValueAsNumber() {
				return Number(this.kmValue);
			},

			celsiusValueAsNumber() {
				return Number(this.celsiusValue);
			},

			fahrenheitValueAsNumber() {
				return Number(this.fahrenheitValue);
			},

			gramsValueAsNumber() {
				return Number(this.gramsValue);
			},

			hektogramsValueAsNumber() {
				return Number(this.hektogramsValue);
			},

			kilogramsValueAsNumber() {
				return Number(this.kilogramsValue);
			},

			tonnesValueAsNumber() {
				return Number(this.tonnesValue);
			},

			secondsValueAsNumber() {
				return Number(this.secondsValue);
			},

			minutesValueAsNumber() {
				return Number(this.minutesValue);
			},

			hoursValueAsNumber() {
				return Number(this.hoursValue);
			},

			daysValueAsNumber() {
				return Number(this.daysValue);
			}
		},

		methods: {
			toggleMenuVisible() {
				this.menuVisible = !this.menuVisible;
				this.menuItem1Visible = false;
				this.menuItem2Visible = false;
				this.menuItem3Visible = false;
				this.menuItem4Visible = false;
			},

			toggleMenuItem1() {
				this.menuItem1Visible = !this.menuItem1Visible;
				this.menuItem4Visible = false;
				this.menuItem3Visible = false;
				this.menuItem2Visible = false;
			},

			toggleMenuItem2() {
				this.menuItem2Visible = !this.menuItem2Visible;
				this.menuItem4Visible = false;
				this.menuItem3Visible = false;
				this.menuItem1Visible = false;
			},

			toggleMenuItem3() {
				this.menuItem3Visible = !this.menuItem3Visible;
				this.menuItem4Visible = false;
				this.menuItem2Visible = false;
				this.menuItem1Visible = false;
			},

			toggleMenuItem4() {
				this.menuItem4Visible = !this.menuItem4Visible;
				this.menuItem3Visible = false;
				this.menuItem2Visible = false;
				this.menuItem1Visible = false;
			},

			calculateInputMM() {
				this.cmValue = this.mmValueAsNumber / 10;
				this.mValue = this.mmValueAsNumber / 1000;
				this.kmValue = this.mmValueAsNumber / 1000000;

				if (this.mmValue === '' || 0) {						
					this.cmValue = '';
					this.mValue = '',
					this.kmValue = '';
				}
			},

			calculateInputCM() {
				this.mmValue = this.cmValueAsNumber * 10;
				this.mValue = this.cmValueAsNumber / 100;
				this.kmValue = this.cmValueAsNumber / 100000;
				this.kmValue = this.cmValueAsNumber / 100000;

				if (this.cmValue === '' || 0) {
						this.mmValue = '';
						this.mValue = '',
						this.kmValue = '';
					}
			},

			calculateInputM() {
				this.mmValue = this.mValueAsNumber * 1000;
				this.cmValue = this.mValueAsNumber * 100;
				this.kmValue = this.cmValueAsNumber / 100000;

				if (this.mValue === '' || 0) {
						this.mmValue = '',
						this.cmValue = '';
						this.kmValue = '';
					}
			},

			calculateInputKM() {
				this.mmValue = this.kmValueAsNumber * 1000000;
				this.cmValue = this.kmValueAsNumber * 100000;
				this.mValue = this.kmValueAsNumber * 1000;

				if (this.kmValue === '' || 0) {
						this.mmValue = '',
						this.cmValue = '';
						this.mValue = '';
					}
			},

			calculateInputCelsius() {
				this.fahrenheitValue = this.celsiusValueAsNumber * 1.8 + 32;

				if (this.celsiusValue === '') {
					this.fahrenheitValue = '';
				}
			},

			calculateInputFahrenheit() {
				this.celsiusValue = (this.fahrenheitValueAsNumber - 32) * 0.5556;

				if (this.fahrenheitValue === '') {
					this.celsiusValue = '';
				}
			},

			calculateInputGrams() {
				this.hektogramsValue = this.gramsValueAsNumber / 100;
				this.kilogramsValue = this.gramsValueAsNumber / 1000;
				this.tonnesValue = this.gramsValueAsNumber / 1000000;

				if (this.gramsValue === '') {
					this.hektogramsValue = '';
					this.kilogramsValue = '';
					this.tonnesValue = '';
				}
			},

			calculateInputHektograms() {
				this.gramsValue = this.hektogramsValueAsNumber * 100;
				this.kilogramsValue = this.hektogramsValueAsNumber / 100;
				this.tonnesValue = this.hektogramsValueAsNumber / 1000000;

				if (this.hektogramsValue === '') {
					this.gramsValue = '';
					this.kilogramsValue = '';
					this.tonnesValue = '';
				}
			},

			calculateInputKilograms() {
				this.gramsValue = this.kilogramsValueAsNumber * 1000;
				this.hektogramsValue = this.kilogramsValueAsNumber * 10;
				this.tonnesValue = this.kilogramsValueAsNumber / 1000;

				if (this.kilogramsValue === '') {
					this.gramsValue = '';
					this.hektogramsValue = '';
					this.tonnesValue = '';
				}
			},

			calculateInputTonnes() {
				this.gramsValue = this.tonnesValueAsNumber * 1000000;
				this.hektogramsValue = this.tonnesValueAsNumber * 10000;
				this.kilogramsValue = this.tonnesValueAsNumber * 1000;

				if (this.tonnesValue === '') {
					this.gramsValue = '';
					this.hektogramsValue = '';
					this.kilogramsValue = '';
				}
			},

			calculateInputSeconds() {
				this.minutesValue = this.secondsValueAsNumber / 60;
				this.hoursValue = this.secondsValueAsNumber / 3600;
				this.daysValue = this.secondsValueAsNumber / 86400;
			},

			calculateInputMinutes() {
				this.secondsValue = this.minutesValueAsNumber * 60;
				this.hoursValue = this.minutesValueAsNumber * 60;
				this.daysValue = this.minutesValueAsNumber / 1440;
			},

			calculateInputHours() {
				this.secondsValue = this.hoursValueAsNumber * 3600;
				this.minutesValue = this.hoursValueAsNumber * 60;
				this.daysValue = this.hoursValueAsNumber / 24;
			},

			calculateInputDays() {
				this.secondsValue = this.daysValueAsNumber * 86400;
				this.minutesValue = this.daysValueAsNumber * 1440;
				this.hoursValue = this.daysValueAsNumber * 24;
			}
		}
	}
</script>

<style>
	.converter {
		width: 100%;
		display: flex;
		flex-flow: column;
		align-items: center;
	}

	.button__converter-menu {
		width: 100%;
		font-size: 40px;
		padding: 10px;
		border: none;
		background-color: #222;
		color: #fff;
		border-radius: 15px;
	}

	.converter__menu-list {
		background-color: #333;
		width: 100%;
		color: #fff;
		border-radius: 15px;
		font-size: 30px;
	}

	.menu-list__items {
		width: 100%;
		border: none;
		display: flex;
		justify-self: start;
		align-items: center;
		padding-left: 10px;
		padding-right: 10px;
		border-radius: 15px;
		background-color: #333;
	}

	.menu-list__items:hover {
		background-color: #555;
	}
	
	.item-1__content {
		width: 100%;
		padding-left: 20px;
		padding-right: 20px;
		background-color: #222;
	}

	.content__container {
		width: 100%;
		padding-top: 20px;
		padding-bottom: 20px;
		font-size: 20px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.content__container input {
		width: 200px;
		height: 40px;
		border: none;
		border-radius: 5px;
		text-align: center;
		font-size: 20px;
	}

	.item-2__content {
		width: 100%;
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		padding: 20px;
		position: relative;
		background-color: #222;
	}

	.input__celsius, .input__fahrenheit {
		width: 150px;
		height: 40px;
		border: none;
		border-radius: 5px;
		text-align: center;
		font-size: 20px;
	}

	.item-2__content span {
		margin-right: 10px;
		margin-left: 10px;
	}
</style>