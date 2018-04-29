<template>
	<div class="search-logo">
		<img :src="LogoSrcs[selectNow].imgsrc" @click="toggleLogo">
		<transition name="logofade">
        <ul v-show="listflag&&inlistflag" class="logoList" @mouseleave="mouseLeaveList">
            <li v-for="(item,index) in SelectSrcs" class="logoItem" @mouseover="logoListHover(index)" :class="{selectlogo:index==logoNow}" @click="logoSelected(index)">
                <img :src="item.imgsrc">
            </li>
        </ul>
    </transition>
	</div>
</template>

<script>

export default {

	data () {
		return {
			selectNow: 0,
			logoNow: -1,
			listflag: false,
			inlistflag: false,
			LogoSrcs: [
				{imgsrc: require('../assets/baidu_s.png')},
				{imgsrc: require('../assets/360_s.png')},
				{imgsrc: require('../assets/sogo_s.png')}
			],
			SelectSrcs: [
				{imgsrc: require('../assets/baidu.png')},
				{imgsrc: require('../assets/360.png')},
				{imgsrc: require('../assets/sogo.png')}
			]
		}
	},
	methods: {

		toggleLogo () {
			this.listflag = !this.listflag;
			this.inlistflag = true
		},

		mouseLeaveList() {
			this.listflag = false;
			this.inlistflag = false;
		},

		logoListHover (index) {
      this.logoNow = index
    },

		logoSelected (index) {
			this.selectNow = index;
			this.$emit('confirmindex', this.selectNow)
		}
	}

}
</script>

<style scoped>
ul{list-style: none;padding: 0;margin: 0}
.search-logo {
	margin-top: 400px;
	position: relative;
}

.search-logo img {
	display: block;
  margin: 0 auto;
  user-select: none;
  cursor: pointer;
}

.logoList {
    position: absolute;
    top: 90%;
    width: 220px;
    left: 50%;
    margin-left: -120px;
    z-index: 999999;
    border: 1px solid #d4d4d4
}

.logoList li {
    width: 100%;
    height: 90px;
    background-color: #fff;
    line-height: 80px;
    padding-top: 1px;
}

.logoList li img {
    width: 100%;
    margin-top: 10px;
}

.selectlogo {
	background-color: #eee !important;
	cursor: pointer
}

.logofade-enter-active, .logofade-leave-active {
    transition: all  .5s;
}

.logofade-enter, .logofade-leave-active {
    opacity: 0;
    transform: translateY(20px);
}

</style>