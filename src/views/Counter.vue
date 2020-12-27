<template>
	<div id="counter">
		<button 
			v-on:click="subNumber"
			v-bind:disabled="bottom_limit_status"
		>-</button>

		<input
			v-bind:value="number"
			v-bind:class="{is_limit: bottom_limit_status || top_limit_status}"
		>

		<button 
			v-on:click="addNumber"
			v-bind:disabled="top_limit_status"
		>+</button>
	</div>
</template>

<script>
export default {
	name: 'Counter',
	data() {
		return {
			number: 0,
			top_limit: 10,
			bottom_limit: 0,
		};
	},
	computed: {
		top_limit_status () {
			return this.number >= this.top_limit
		},
		bottom_limit_status () {
			return this.number <= this.bottom_limit
		}
	},
	methods: {
		addNumber: function () {
			this.number = this.number + 1;
		},
		subNumber: function () {
			this.number = this.number - 1;
		},

	}
}
</script>

<style scoped>
#counter {
	width: 100vw;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
}
button {
	margin: 10px;
	width: 40px;
	height: 40px;
	border-radius: 25px;
	border:none;
	background-color: black;
	color:white;
}
input {
	text-align: center;
	height: 20px;
	width: 100px;
}

.is_limit{
	background-color: #d65740;
}

</style>
