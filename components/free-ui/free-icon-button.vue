<template>
	<view class="flex align-center justify-center" hover-class="bg-hover-light" style="height: 90rpx;width: 90rpx;" @click="$emit('click')">
		<text class="iconfont font-md">
			<slot></slot>
		</text>
	</view>
</template>

<script>
</script>

<style>
</style>