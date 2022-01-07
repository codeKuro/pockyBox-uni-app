<template>
	<view class="u-wrap">
		<u-navbar title-color="#fff" back-icon-color="#ffffff" :is-fixed="isFixed" :is-back="isBack"
			:background="background" :back-text-style="{color: '#fff'}" :title="title" :back-icon-name="backIconName"
			:back-text="backText">
			<view class="slot-wrap" v-if="useSlot">
				<view class="map-wrap" v-if="custom">
					<u-icon name="map" color="#ffffff" size="24"></u-icon>
					<text class="map-wrap-text">设置并授权地理位置</text>
					<!-- <u-icon name="arrow-down-fill" color="#ffffff" size="22"></u-icon> -->
				</view>
				<view class="navbar-right" v-if="rightSlot">
					<view class="message-box right-item">
						<u-icon name="chat" size="38"></u-icon>
						<u-badge count="18" size="mini" :offset="[-15, -15]"></u-badge>
					</view>
					<view class="dot-box right-item">
						<u-icon name="share" size="38"></u-icon>
						<!-- <u-badge size="mini" :is-dot="true" :offset="[-6, -6]"></u-badge> -->
					</view>
				</view>
			</view>
		</u-navbar>


		<view class="u-banner">
			<u-toast ref="uToast"></u-toast>
			<u-swiper @change="change" :height="250" :list="list" :title="titles" :indicator-pos="indicatorPos"
				:mode="mode" :interval="3000"></u-swiper>
		</view>
		<view class="u-content">
			<view class="u-config-item">
				<view class="u-item-title">精选奖品</view>
				<view class="see-more">查看更多</view>
			</view>
			<u-row class="u-mall-list" justify="between">
				<u-col class="u-mall-item" span="3" v-for="(item,index) in mallList" stop>
					<image :src="item.image" mode=""></image>
				</u-col>
			</u-row>
			<view class="u-config-item">
				<view class="u-item-title">我的待开盲盒</view>
				<view class="see-more">查看更多</view>
			</view>

			<view class="u-box-list">
				<view class="">
					我的盲盒:{{boxNum}}个
				</view>
				<u-row class="u-mall-list" justify="between">
					<u-col class="u-mall-item" span="3" v-for="(item,index) in boxList" stop>
						<image :src="item.image" mode=""></image>
					</u-col>
				</u-row>
			</view>
			<view class="u-button-area">
				<u-button type="primary">立即开盒</u-button>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				list: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
				mallList: [{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
				boxList: [{
					image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
					title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
				}, {
					image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
					title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
				}, {
					image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
					title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
				}, {
					image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
					title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
				}],

				titles: false,
				title: '',
				backText: '返回',
				backIconName: 'nav-back',
				right: false,
				showAction: false,
				rightSlot: true,
				useSlot: true,
				background: {
					'background-image': 'linear-gradient(45deg, rgb(248, 89, 229), rgb(248, 89, 229))'
				},
				isBack: false,
				search: false,
				custom: true,
				isFixed: true,
				mode: 'round',
				indicatorPos: 'bottomCenter',
				boxNum: 25,
			}
		},
		methods: {
			change(index) {
				//console.log(index);
			}
		}
	}
</script>

<style lang="scss" scoped>
	.navbar-right {
		margin-right: 24rpx;
		display: flex;
	}
	
	.search-wrap {
		margin: 0 20rpx;
		flex: 1;
	}
	
	.right-item {
		margin: 0 12rpx;
		position: relative;
		color: #ffffff;
		display: flex;
	}
	
	.slot-wrap {
		display: flex;
		align-items: center;
		flex: 1;
		justify-content: space-between;
	}
	
	.map-wrap {
		display: flex;
		align-items: center;
		padding: 4px 6px;
		background-color: rgba(240,240, 240, 0.35);
		color: #fff;
		font-size: 22rpx;
		border-radius: 100rpx;
		margin-left: 30rpx;
	}
	
	.map-wrap-text {
		padding: 0 6rpx;
	}
	.u-config-item {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.u-item-title {
		margin-bottom: 0;
	}

	.u-item-title:after {
		background-color: #55aaff;
	}

	.see-more {
		font-size: 12px;
		color: #55aaff;
	}

	.u-mall-list {
		display: flex;
		justify-content: flex-start;
		align-items: center;
		flex-wrap: nowrap;
		overflow-x: auto;
		overflow-y: hidden;
		padding: 4px;
	}

	.u-mall-item {
		flex-shrink: 0;
	}

	.u-mall-item image {
		width: 100%;
	}

	.u-button-area {
		padding: 20px 10px;
	}
</style>
