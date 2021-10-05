<template>
	<div class="app-wrapper">
		<ImgCp :title="title" :src="src"/>
		<ul class="thumb-wrap">
			<ThumbCp v-for="v in foods" :key="v.id" :img="v" @@change="onChange" />
		</ul>
	</div>
</template>

<script>
/* 
1. 부모 컴포넌트가 자식 컴포넌트에게 변수를 전달할 때는 v-bind로 전달한다.
2. 자식 컴포넌트는 부모로 부터 props로 변수를 전달 받는다.
3. 자식 컴포넌트가 부모 컴포넌트에게 변수를 전달할 때는 event로 전달한다.
4. 부모 컴포넌트는 자식으로 부터 v-on으로 이벤트를 통한 변수를 전달 받는다.
*/
// export default 는 한개만 보내는거 -> module.exports = () => {}
// export 는 보내는거 -> module.exports = { ?, ? }
import axios from 'axios'
import ImgCp from './components/imgCp.vue'
import ThumbCp from './components/ThumbCp.vue'


export default {
	name: 'App',
	components: { ImgCp, ThumbCp },
	data() {
		return {
			foods: [],
			title: '',
			src: '',
		}
	},
	methods: {
		onChange(v) {
			this.src = v.src
			this.title = v.title
		}
	},
	async created() {
		const { data } = await axios.get('/json/foods.json')
		this.foods = data
		this.title = this.foods[0].title
		this.src = this.foods[0].src
	},
}
</script>

<style lang="scss">
ul, ol {
	list-style: none;
}
	.app-wrapper {
		max-width: 400px;
		margin: 2em auto 1em auto;
		.thumb-wrap {
			border: 1px solid #efefef;
			border-radius: .325em;
			padding: .5em;
			display: flex;
			width: 101%;
			cursor: pointer;
		}
	}
</style>