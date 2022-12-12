<template>	
	<section class="calculator">
		<div class="calculator__output">
			{{ currentOutput || 0 }}
		</div>

		<div class="calculator__inputs">
			<button @click="clear" class="inputs__button clear">C</button>
			<button @click="percentage" class="inputs__button operator">%</button>
			<button @click="positiveNegativeSwitch" class="inputs__button operator">+/-</button>
			<button @click="division" class="inputs__button operator">/</button>
			<button @click="digitInputs('7')" class="inputs__button ">7</button>
			<button @click="digitInputs('8')" class="inputs__button ">8</button>
			<button @click="digitInputs('9')" class="inputs__button ">9</button>
			<button @click="multiplication" class="inputs__button operator">x</button>
			<button @click="digitInputs('4')" class="inputs__button ">4</button>
			<button @click="digitInputs('5')" class="inputs__button ">5</button>
			<button @click="digitInputs('6')" class="inputs__button ">6</button>
			<button @click="subtraction" class="inputs__button operator">-</button>
			<button @click="digitInputs('1')" class="inputs__button ">1</button>
			<button @click="digitInputs('2')" class="inputs__button ">2</button>
			<button @click="digitInputs('3')" class="inputs__button ">3</button>
			<button @click="addition" class="inputs__button operator">+</button>
			<button @click="digitInputs('0')" class="inputs__button ">0</button>
			<button @click="getComma" class="inputs__button comma">.</button>
			<button @click="equals" class="inputs__button equals">=</button>
		</div>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				currentOutput: '',
				operator: null,
				operatorClicked: false,
				previousValue: 0,
			}
		},

		computed: {
			currentOutputAsNumber() {
				return Number(this.currentOutput);
			},

			previousValueAsNumber() {
				return Number(this.previousValue);
			}
		},
		
		methods: {
			zero() {
				if (this.currentOutput[0] === '0') {
					this.currentOutput = this.currentOutput.slice(1);
				}
			},
			
			clear () {
				this.currentOutput = '';
				this.operator = null;
				this.operatorClicked = false;
				this.previousValue = 0;
			},

			percentage() {
				this.currentOutput = this.currentOutputAsNumber / 100;
			},

			positiveNegativeSwitch() {
				this.currentOutput = this.currentOutput * -1;
			},

			digitInputs(number) {
				this.zero()
				if (this.operatorClicked) {
					this.currentOutput = '';
					this.operatorClicked = false;
				}
				this.currentOutput += number;
			},

			addition() {
				this.operator = (previousInput, currentInput) => previousInput + currentInput;
				this.operatorClicked = true;
				this.previousValue = this.currentOutput;
			},

			subtraction() {
				this.operator = (previousInput, currentInput) => previousInput - currentInput;
				this.operatorClicked = true;
				this.previousValue = this.currentOutput;
			},

			division() {
				this.operator = (previousInput, currentInput) => previousInput / currentInput;
				this.operatorClicked = true;
				this.previousValue = this.currentOutput;
			},

			multiplication() {
				this.operator = (previousInput, currentInput) => previousInput * currentInput;
				this.operatorClicked = true;
				this.previousValue = this.currentOutput;
			},

			getComma() {
				if (this.currentOutput.indexOf('.') === -1) {
					this.currentOutput = this.currentOutput + '.';
				}

				if (this.currentOutput[0] === '.') {
					this.currentOutput = this.currentOutput.slice(1);
				}
			},

			equals() {
				this.currentOutput = this.operator(this.previousValueAsNumber, this.currentOutputAsNumber);
			},
		}
	}
</script>
	
<style>
	.calculator {
		margin-top: 50px;
		width: 400px;
		display: flex;
		flex-flow: column;
		background-color: #222;
		border-radius: 15px;
		height: 550px;
		padding: 10px;
	}

	.calculator__output {
		background-color: #444;
		border-radius: 15px;
		font-size: 40px;
		color: #fff;
		width: 100%;
		height: 100px;
		display: flex;
		justify-content: end;
		align-items: center;
		padding: 10px;
	}

	.calculator__inputs {
		width: 100%;
		margin-top: 10px;
		height: 100%;
		border-radius: 15px;
		display: grid;
		grid-template-columns: repeat(4, 25%);
	}

	.inputs__button {
		align-self: center;
		justify-self: center;
		width: 80px;
		height: 80px;
		border-radius: 15px;
		background-color: #d3d3d3;
		font-size: 30px;
	}

	.equals {
		background-color: rgb(185, 255, 185);
		font-size: 3	0px;
		font-weight: 700;
		width: 170px;
		grid-column: 3 / 5;
	}

	.clear {
		background-color: rgb(255, 179, 179);
		font-size: 30px;
		font-weight: 700;
	}

	.operator {
		background-color: rgb(255, 245, 173);
		font-size: 30px;
		font-weight: 700;
	}
</style>