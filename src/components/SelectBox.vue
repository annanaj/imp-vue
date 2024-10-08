<template>
	<div class="wrapper">
		<select v-model="name">
			<option>one</option>
			<option>two</option>
			<option>three</option>
			<option>four</option>
		</select>
		<p v-if="name">I choose {{ name }}</p>
	</div>
</template>

<script>
export default {
	name: 'SelectBox',
};
</script>

<style scoped>
.wrapper {
    display: flex;
    justify-content: center;
    padding-bottom: 30px;
    border-bottom: 1px solid #ccc;
}

select {
    width: 100px;
}

</style>
