<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png">
		<Calc msg="Calculator"/>
	</div>
</template>

<script>
	import Calc from './components/Calc.vue';
	export default {
		name: 'app',
		components: {
			Calc
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
	img {
		height: 50px;
		width: 50px;
	}
</style>
