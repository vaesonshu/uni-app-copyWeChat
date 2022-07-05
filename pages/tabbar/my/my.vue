<template>
	<view class="page">
		<free-nav-bar bgColor="bg-white">
			<free-icon-button slot="right">&#xe6ed;</free-icon-button>
		</free-nav-bar>
		<free-list-item cover="../../../static/images/userpic.png" title="松鼠" coverSize="120" showRight>
			<view class="flex flex-column">
				<text class="text-dark font-lg font-weight-bold">松鼠</text>
				<text class="text-light-muted font mt-2">仿微信号：vaeian</text>
			</view>
			<view slot="right">
				<text class="iconfont font-md text-light-muted" style="padding-top: 60rpx;">&#xe614;</text>
			</view>
		</free-list-item>
		<free-divider></free-divider>
		<free-list-item title="支付" showRight>
			<text slot="icon" class="iconfont font-lg py-1 navStyle">&#xe66c;</text>
		</free-list-item>
		<free-divider></free-divider>
		<free-list-item title="收藏" showRight>
			<text slot="icon" class="iconfont font-lg py-1 navStyle">&#xea2d;</text>
		</free-list-item>
		<free-list-item title="相册" showRight>
			<text slot="icon" class="iconfont font-lg py-1 navStyle">&#xe608;</text>
		</free-list-item>
		<free-list-item title="表情" showRight>
			<text slot="icon" class="iconfont font-lg py-1 navStyle">&#xe605;</text>
		</free-list-item>
		<free-divider></free-divider>
		<free-list-item title="设置" showRight>
			<text slot="icon" class="iconfont font-lg py-1 navStyle">&#xe612;</text>
		</free-list-item>
	</view>
</template>

<script>
	import freeNavBar from '@/components/free-ui/free-nav-bar.vue'
	import freeIconButton from '@/components/free-ui/free-icon-button.vue'
	import freeListItem from '@/components/free-ui/free-list-item.vue'
	import freeDivider from '@/components/free-ui/free-divider.vue'
	export default {
		components: {
			freeNavBar,
			freeIconButton,
			freeListItem,
			freeDivider
		},
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.navStyle {
	font-size: 40rpx;padding-top: 25rpx;
}
</style>
