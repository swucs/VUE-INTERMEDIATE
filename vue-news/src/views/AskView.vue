<template>
	<div>
		<p v-for="item in fetchedAsk" v-bind:key="item.id">
			<!-- <a :href="item.url"> -->
			<router-link v-bind:to="`item/${item.id}`">
				{{ item.title }}
			</router-link>
			<!-- </a> -->
			<small>
				{{ item.time_ago }} by {{ item.user }}
			</small>
		</p>
	</div>
</template>

<script>
import { mapState, mapGetters } from 'vuex';

export default {
	computed : {
		...mapGetters([
			'fetchedAsk'
		]),
		// ...mapState({
		// 	ask : state => state.ask
		// })
	},
	created() {
		this.$store.dispatch('FETCH_ASK');
	},
}
</script>

<style>

</style>