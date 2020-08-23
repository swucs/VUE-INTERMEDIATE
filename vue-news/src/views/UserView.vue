<template>
	<div>
		<p>name : {{ userinfo.id }}</p>
		<p>karma : {{ userinfo.karma }}</p>
		<p>created : {{ userinfo.created }}</p>
	</div>
</template>

<script>

export default {
	computed: {
		userinfo() {
			return this.$store.state.user;
		}
	},
	created() {
		const username = this.$route.params.id;
		this.$store.dispatch('FETCH_USER', username);
	},
	
}
</script>

<style>

</style>