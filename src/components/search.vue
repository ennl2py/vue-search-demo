<template>
	<div>
		<logo-select @confirmindex="confirmIndex"></logo-select>
		<div class="search-part">
			<input type="text" v-model="kwords" @keydown.enter="startSearch">
			<button class="search-btn" @click="startSearch">搜索</button>
		</div>
	</div>
</template>

<script>
import LogoSelect from "./selectlogo"

export default {
	components: {
		LogoSelect
	},
	data () {
		return {
			urls: [
				{url: 'https://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&rsv_idx=1&tn=baidu&wd='},
				{url: 'https://www.so.com/s?ie=utf-8&fr=none&q='},
				{url: 'https://www.sogou.com/web?query='}
			],
			sindex: 0,
			kwords:''
		}
	},
	methods: {
		confirmIndex (index) {
			this.sindex = index
		},
		startSearch () {
			if (this.kwords) {
				window.open(this.urls[this.sindex].url + this.kwords)
			}
			else {
				alert('请输入想要搜索的关键字哦!')
			}
		}
	}
}
</script>

<style scoped>
.search-part {
	font-size: 0
}

.search-part input {
	height: 35px;
	width:	540px;
	box-sizing: border-box;
	margin: 0;
	padding: 0 8px;
	border: 1px solid #d3d3d3;
	font-size: 20px
}	

.search-btn {
	height: 35px;
	width:	100px;
	margin: 0;
	font-size: 18px;
	background-color: #4682b4;
	border: 1px solid #4682b4;
	color: #fff;
	cursor: pointer
}
</style>