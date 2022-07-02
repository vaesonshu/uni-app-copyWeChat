<template>
	<view :class="item.istop ? 'bg-light' : 'bg-white'" hover-class="bg-light">
		<div class="flex align-stretch" @click="onClick" @longpress="long">
			<view class="flex align-center justify-center position-relative" style="width: 145rpx;">
				<free-avatar :src="item.avatar" size="92"></free-avatar>
				<free-badge badgeClass="position-absolute" badgeStyle="top:15rpx;right:15rpx" v-if="item.noreadnum" :value="item.noreadnum"></free-badge>
			</view>
			<view class="flex flex-column border-bottom flex-1 py-3 pr-3 border-light-secondary">
				<view class="flex align-center justify-between mb-1">
					<text class="font-md">{{item.nickname}}</text>
					<text class="font-sm text-light-muted">{{item.update_time | formatTime}}</text>
				</view>
				<text class="font text-ellipsis text-light-muted">{{item.data}}</text>
			</view>
		</div>
	</view>
</template>

<script>
	import freeBase from '@/common/mixin/free-base.js'
	import freeAvatar from '@/components/free-ui/free-avatar.vue'
	import freeBadge from '@/components/free-ui/free-badge.vue'
	export default {
		mixins: [freeBase],
		props: {
			item: Object,
			index: Number
		},
		components: {
			freeAvatar,
			freeBadge
		},
		methods: {
			onClick() {
				this.$emit('click')
				console.log('点击事件')
			},
			long(e) {
				let x = 0
				let y = 0
				// #ifdef APP-PLUS-NVUE
				if(Array.isArray(e.changedTouches) && e.changedTouches.length > 0) {
					x = e.changedTouches[0].screenX
					y = e.changedTouches[0].screenY
					console.log(x,y)
				}
				console.log('NVUE')
				// #endif
				// #ifdef H5
				x = e.changedTouches[0].pageX
				y = e.changedTouches[0].pageY
				console.log('H5')
				// #endif
				// 小程序端
				// #ifdef MP
				x = e.detail.x
				y = e.detail.y
				console.log('MP')
				// #endif
				this.$emit('long', {x, y, index: this.index})
			}
		}
	}
</script>

<style>
</style>