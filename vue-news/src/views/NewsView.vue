<template>
	<div>
		<ul class="news-list">
			<li v-for="item in this.$store.state.news" v-bind:key="item.id" class="post">
				<div class="points">
					{{ item.points }}
				</div>

				<div>
					<p class="news-title">
						<a v-bind:href="item.url">
							{{ item.title }}
						</a>
					</p>
					<small class="link-text">
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
export default {
	created() {
		this.$store.dispatch('FETCH_NEWS');
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
