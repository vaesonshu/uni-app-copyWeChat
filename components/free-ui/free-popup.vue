<template>
	<div style="z-index: 9999;overflow: hidden;" v-if="status">
		<!-- 蒙板 -->
		<div v-if="showMask" class="position-fixed top-0 left-0 right-0 bottom-0" :style="getMaskColor" @click="hide"></div>
		<!-- 弹出框内容 -->
		<div ref="popup" class="position-fixed free-animated" :class="getBodyClass" :style="getBodyStyle">
			<slot></slot>
		</div>
	</div>
</template>

<script>
	// #ifdef APP-PLUS-NVUE
	const animation = weex.requireModule('animation')
	// #endif
	export default {
		props: {
			// 是否展示蒙板
			showMask: {
				type: Boolean,
				default: true
			},
			// 是否展示蒙板颜色
			showMaskColor: {
				type: Boolean,
				default: false
			},
			// 是否处于底部
			fixedBottom: {
				type: Boolean,
				default: false
			},
			// 弹出层内容宽度
			bodyWidth: {
				type: Number,
				default: 0
			},
			// 弹出层内容高度
			bodyHeight: {
				type: Number,
				default: 0
			},
			bodyBgColor: {
				type: String,
				default: 'bg-white'
			},
			transformOrigin: {
				type: String,
				default: 'left top'
			}
		},
		data() {
			return {
				status: false,
				x: -1,
				y: -1,
				maxX: 0,
				maxY: 0
			}
		},
		mounted() {
			try{
				const res = uni.getSystemInfoSync()
				this.maxX = res.windowWidth - uni.upx2px(this.bodyWidth)
				this.maxY = res.windowHeight - uni.upx2px(this.bodyHeight)
			}catch(e){
				//TODO handle the exception
			}
		},
		computed: {
			getMaskColor() {
				let a = this.showMaskColor ? 0.5 : 0
				return `background-color: rgba(0, 0, 0, ${a});`
			},
			getBodyClass() {
				let fixedBottom = this.fixedBottom ? 'left-0 right-0 bottom-0' : 'rounded border'
				return `${this.bodyBgColor} ${fixedBottom}`
			},
			getBodyStyle() {
				let left = this.x > -1 ? `left:${this.x}px;` : ''
				let top = this.y > -1 ? `top:${this.y}px;` : ''
				return left + top
			}
		},
		methods: {
			show(x = -1, y = -1) {
				this.x = (x > this.maxX) ? this.maxX : x
				this.y = (y > this.maxY) ? this.maxY : y
				this.status = true
				// #ifdef APP-PLUS-NVUE
				this.$nextTick(()=>{
					animation.transition(this.$refs.popup, {
					    styles: {
					        transform: 'scale(1,1)',
							transformOrigin:this.transformOrigin,
							opacity:1
					    },
					    duration: 100, //ms
					    timingFunction: 'ease',
					    }, function () {
					       console.log('动画执行结束');
					    })
				})
				// #endif
			},
			hide() {
				// #ifdef APP-PLUS-NVUE
				animation.transition(this.$refs.popup, {
				styles: {
					transform: 'scale(0,0)',
					transformOrigin:this.transformOrigin,
					opacity:0
				},
				duration: 100, //ms
				timingFunction: 'ease',
				}, ()=> {
					this.status = false
				   console.log('动画执行结束');
				})
				// #endif
				this.status = false
			}
		}
	}
</script>

<style scoped>
	.free-animated {
		/* #ifdef APP-PLUS-NVUE */
		transform: scale(0, 0);
		opacity: 0;
		/* #endif */
	}
</style>