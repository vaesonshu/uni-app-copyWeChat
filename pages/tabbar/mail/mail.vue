<template>
	<view>
		<!-- 导航栏 -->
		<free-nav-bar title="通讯录"></free-nav-bar>
		
		<!-- 通讯录列表 -->
		<free-list-item v-for="(item, index) in topList" :key="index" :cover="item.cover" :title="item.title"></free-list-item>
		
		<block v-for="(item, index) in list" :key="index">
			<view class="" v-if="item.data.length">
				<view class="py-2 px-3 border-bottom bg-light">
					<text class="font-md text-dark">{{item.letter}}</text>
				</view>
				<free-list-item v-for="(item2, index2) in item.data" :key="index2" cover="/static/images/mail/tag.png" :title="item2"></free-list-item>
			</view>
		</block>
		
	</view>
</template>

<script>
	import freeNavBar from '@/components/free-ui/free-nav-bar.vue'
	import freeListItem from '@/components/free-ui/free-list-item.vue'
	export default {
		components: {
			freeNavBar,
			freeListItem
		},
		data() {
			return {
				topList: [
					{
						title: "新的朋友",
						cover: "/static/images/mail/friend.png",
						event: ""
					},
					{
						title: "群聊",
						cover: "/static/images/mail/group.png",
						event: ""
					},
					{
						title: "标签",
						cover: "/static/images/mail/tag.png",
						event: ""
					}
				],
				list: [
					{
						"letter": "A",
						"data": [
							"阿明",
							"阿郎"
						]
					},
					{
						"letter": "B",
						"data": [
							"别具一格",
							"别致"
						]
					},
					{
						"letter": "C",
						"data": [
							"参考",
							"参谋"
						]
					},
					{
						"letter": "D",
						"data": []
					},
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
