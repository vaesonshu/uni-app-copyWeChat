<template>
	<view class="">
		<!-- 导航栏 -->
		<free-nav-bar title="仿微信" :noreadnum="10">
		</free-nav-bar>
		<!-- 置顶列表 -->
		<block v-for="(item, index) in list" :key="index">
			<free-media-list v-if="item.istop" :item="item" :index="index" @long="long"></free-media-list>
		</block>
		<!-- 非置顶列表 -->
		<block v-for="(item, index) in list" :key="index">
			<free-media-list v-if="!item.istop" :item="item" :index="index" @long="long"></free-media-list>
		</block>
		<!-- 弹出层 -->
		<free-popup ref="extend" :bodyWidth="240" :bodyHeight="getMenusHeight">
			<view class="flex flex-column" style="width: 240rpx;" :style="getMenusStyle">
				<view class="flex-1 flex align-center" hover-class="bg-light" v-for="(item, index) in menus" :key="index" @click="clickEvent(item.event)">
					<text class="font-md pl-3">{{item.name}}</text>
				</view>
			</view>
		</free-popup>
	</view>
</template>

<script>
	import freeNavBar from '@/components/free-ui/free-nav-bar.vue'
	import freeMediaList from '@/components/free-ui/free-media-list.vue'
	import freePopup from '@/components/free-ui/free-popup.vue'
	export default {
		components: {
			freeNavBar,
			freeMediaList,
			freePopup
		},
		data() {
			return {
				propIndex: -1,
				menus: [
					{
						name: "设为置顶",
						event:"setTop"
					},
					{
						name: "删除该聊天",
						event:"delChat"
					}
				],
				list: [
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian111",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 1,
						istop: true
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian222",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 1,
						istop: true
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian333",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 1,
						istop: true
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian444",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 2,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian555",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					},
					{
						avatar: "/static/images/extends/man.png",
						nickname: "vaeian",
						update_time: 1567694767,
						data: "程序猿松鼠",
						noreadnum: 3,
						istop: false
					}
					
				]
			}
		},
		onLoad() {
			
		},
		computed: {
			getMenusHeight() {
				let h = 100
				return this.menus.length * h
			},
			getMenusStyle() {
				return `height: ${this.getMenusHeight}rpx`
			}
			
		},
		methods: {
			long({x, y, index}) {
				this.propIndex = index
				// 判断之前是否处于置顶状态
				let item = this.list[index]
				this.menus[0].name = item.istop ? '取消置顶' : '设为置顶'
				this.$refs.extend.show(x, y)
			},
			// 分发菜单事件
			clickEvent(event) {
				switch (event) {
					case "setTop": // 置顶/取消置顶会话
					this.setTop()
					break;
					case "delChat": // 删除当前会话
					this.delChat()
					break;
				}
				this.$refs.extend.hide()
			},
			// 删除当前会话
			delChat() {
				this.list.splice(this.propIndex, 1)
			},
			// 置顶/取消置顶会话
			setTop() {
				let item = this.list[this.propIndex]
				item.istop = !item.istop
			}
		}
	}
</script>

<style>

</style>
