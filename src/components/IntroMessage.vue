<template>
	<div>
		<h1 class="h3">{{ msg }}</h1>
	</div>
</template>

<script>
export default {
	name: 'IntroMessage',
	props: {
		msg: String
	}
}
</script>

<style scoped>
.h3 {
    text-align: center;
	font-size: 24px;
    font-weight: bold;
}

ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
</style>
