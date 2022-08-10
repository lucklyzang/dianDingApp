<template>
	<div class="content-box" id="top-content">
		<NavBar path="/myInfo" title="关于我们"/>
		<div class="content-top">
            <img :src="logoScriptPng">
		</div>
		<div class="content-center">
			点丁数字藏品平台，简称点丁数藏，是点丁数藏科技旗下的数字藏品发行平台。点丁数藏愿景是不断满足用户对数字藏品的收藏与分享交流的需要，竭力把文化艺术等各个领域的优质IP数字化，平民化，让越来越多的人接触认识和推广数字藏品。点丁数藏由斐德坊链提供全面技术支持。
		</div>
		<div class="content-bottom">
			<span>
                V0.1.0
            </span>
		</div>
	</div>
</template>

<script>
	import {
		mapGetters,
		mapMutations
	} from 'vuex'
	import NavBar from '@/components/NavBar'
	export default {
		name: 'AboutUs',
		components: {
            NavBar
		},
		data() {
			return {
			  logoScriptPng: require("@/common/images/home/default-person.png")
			}
		},
		onReady() {},
		computed: {
			...mapGetters([
			])
		},
		mounted() {
			this.toTop();
			// 控制设备物理返回按键
            if (!IsPC()) {
                pushHistory();
                this.gotoURL(() => {
                pushHistory();
                    this.$router.push({
                        path: '/myInfo'
                    })
                })
            };
		},
		methods: {
			...mapMutations([
			]),
			//让页面滚动到顶部
			toTop() {
				document.querySelector('#top-content').scrollIntoView(true)
			}
		}
	}
</script>

<style lang="less" scoped>
	@import "~@/common/stylus/variable.less";
    @import "~@/common/stylus/mixin.less";
    @import "~@/common/stylus/modifyUi.less";
	.content-box {
		.content-wrapper();
        background: @color-background;
        /deep/ .van-nav-bar {
            .van-icon {
                color: #fff !important;
                font-size: 18px !important
            };
            .van-nav-bar__title {
                color: #fff !important;
                font-size: 16px !important
            }
        };
		.content-top {
			height: 200px;
			display: flex;
			margin-top: 30px;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			img {
				width: 160px
			}
		};
		.content-center {
			width: 90%;
			margin: 0 auto;
			flex: 1;
			overflow: auto;
			color: #686868;
			font-size: 15px;
			line-height: 20px;
			text-indent: 2em;
			text-align: justify
		};
		.content-bottom {
			height: 60px;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			> span {
				&:nth-child(1) {
                    font-size: 14px;
                    color: #a9a9a9
                }
			}
		}
	}
</style>




