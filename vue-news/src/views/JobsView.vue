<template>
	<div>
		<ul class="news-list">
			<li v-for="item in this.$store.state.jobs" v-bind:key="item.id" class="post">
				

				<div>
					<p class="news-title">
						<a :href="item.url">
							{{ item.title }}
						</a>
					</p>
					<small class="link-text">
						{{ item.time_ago }} by 
						<a :href="item.url">{{ item.domain }}</a>
					</small>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	created() {
		this.$store.dispatch('FETCH_JOBS');
	}
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