<template>
	<Converter />
	<Calculator/>
</template>

<script>
	import Converter from '../components/Converter.vue'
	import Calculator from '../components/Calculator.vue'

	export default {
		components: {
			Converter,
			Calculator,
		}
	}
</script>

<style>
	@import '../../css/reset.css';
	@import '../../css/style.css';
	@import 'https://fonts.googleapis.com/css?family=Poppins';
	
	body {
		width: 100%;
		max-width: 1200px;
		margin: auto;
		background-color: #d3d3d3;
		display: flex;
		justify-content: center;
		align-items: center;
		font-family: 'Poppins';
	}
</style>