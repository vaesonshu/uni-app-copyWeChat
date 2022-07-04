<template>
	<view class="page">
		<!-- 导航栏 -->
		<free-nav-bar title="发现"></free-nav-bar>
		<free-list-item title="朋友圈" showRight>
			<text slot="icon" class="iconfont font-lg" style="font-size: 40rpx;padding-top: 10rpx;">&#xe667;</text>
			<view slot="right" class="position-relative p-1">
				<free-avatar src="/static/images/mail/friend.png" size="55"></free-avatar>
				<text class="rounded-circle bg-danger position-absolute" style="width: 20rpx;height: 20rpx;top: 0;right: 0;"></text>
			</view>
		</free-list-item>
		<free-divider></free-divider>
		<free-list-item title="朋友圈" showRight>
			<text slot="icon" class="iconfont font-lg py-1">&#xe667;</text>
		</free-list-item>
		<free-list-item title="朋友圈" showRight>
			<text slot="icon" class="iconfont font-lg py-1">&#xe667;</text>
		</free-list-item>
		<free-divider></free-divider>
		<free-list-item title="朋友圈" showRight>
			<text slot="icon" class="iconfont font-lg py-1">&#xe667;</text>
		</free-list-item>
		<free-list-item title="朋友圈" showRight>
			<text slot="icon" class="iconfont font-lg py-1">&#xe667;</text>
		</free-list-item>
		<free-divider></free-divider>
		<free-list-item title="朋友圈" showRight>
			<text slot="icon" class="iconfont font-lg py-1">&#xe667;</text>
		</free-list-item>
	</view>
</template>

<script>
	import freeNavBar from '@/components/free-ui/free-nav-bar.vue'
	import freeListItem from '@/components/free-ui/free-list-item.vue'
	import freeAvatar from '@/components/free-ui/free-avatar.vue'
	import freeDivider from '@/components/free-ui/free-divider.vue'
	export default {
		components: {
			freeNavBar,
			freeListItem,
			freeAvatar,
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

</style>
