<template>
	<div>
		<ul class="news-list">
			<li v-for="item in fetchedAsk" v-bind:key="item.id" class="post">
				<div class="points">
					{{ item.points }}
				</div>

				<div>
					<router-link v-bind:to="`item/${item.id}`">
						{{ item.title }}
					</router-link>
					<!-- </a> -->
					<small>
						{{ item.time_ago }} 
						by 
						<router-link v-bind:to="`/user/${item.user}`" class="link-text">{{ item.user }}</router-link>
					</small>
				</div>
				
			</li>
		</ul>
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

<style scoped>
	.news-list {
		margin : 0;
		padding : 0;
	}
	.post {
		list-style: none;
		display: flex;
		align-items: center;
		border-bottom: 1px solid  #c2bfbf;
	}
	.points {
		width: 80px;
		height: 60px;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #41b883;
	}
	.news-title {
		margin: 0;
	}
	.link-text {
		color : #828282
	}
</style>