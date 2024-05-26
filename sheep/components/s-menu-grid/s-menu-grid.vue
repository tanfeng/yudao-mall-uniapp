<!-- 装修基础组件：宫格导航 -->
<template>
	<uni-grid :showBorder="Boolean(data.border)" :column="data.column">
		<uni-grid-item v-for="(item, index) in data.list" :key="index" @tap="sheep.$router.go(item.url)">
			<view class="grid-item-box ss-flex ss-flex-col ss-row-center ss-col-center">
				<view class="img-box">
					<view class="tag-box" v-if="item.badge.show"
						:style="[{ background: item.badge.bgColor, color: item.badge.textColor }]">
						{{ item.badge.text }}
					</view>
					<image class="menu-image" :src="sheep.$url.cdn(item.iconUrl)"></image>
				</view>

				<view class="title-box ss-flex ss-flex-col ss-row-center ss-col-center">
					<view class="grid-text" :style="[{ color: item.titleColor }]">
						{{ item.title }}
					</view>
					<view class="grid-tip" :style="[{ color: item.subtitleColor }]">
						{{ item.subtitle }}
					</view>
				</view>
			</view>
		</uni-grid-item>
		<uni-grid-item>

			<view class="grid-item-box ss-flex ss-flex-col ss-row-center ss-col-center">
				<button open-type="contact" style="position: absolute;opacity: 0;z-index: 3;">点击联系客服</button>
				<view class="img-box">
					<view class="tag-box" v-if="userList.badge.show"
						:style="[{ background: userList.badge.bgColor, color: userList.badge.textColor }]">
						{{ userList.badge.text }}
					</view>
					<image class="menu-image" :src="sheep.$url.cdn(userList.iconUrl)"></image>
				</view>

				<view class="title-box ss-flex ss-flex-col ss-row-center ss-col-center">
					<view class="grid-text" :style="[{ color: userList.titleColor }]">
						{{ userList.title }}
					</view>
					<view class="grid-tip" :style="[{ color: userList.subtitleColor }]">
						{{ userList.subtitle }}
					</view>
				</view>
			</view>


		</uni-grid-item>
	</uni-grid>
</template>

<script setup>
	import sheep from '@/sheep';

	const props = defineProps({
		data: {
			type: Object,
			default () {},
		},
	});
	const userList = {
		badge: {
			show: false,
			textColor: "#fff",
			bgColor: "#FF6000"
		},
		iconUrl: "https://file.sheepjs.com/storage/decorate/20221115/3c7eb06563d1cf28b4b34bb0d1647659.png",
		subtitle: "",
		subtitleColor: "#bbb",
		title: "联系客服",
		titleColor: "#333",
		url: "/pages/chat/index"
	};
</script>

<style lang="scss" scoped>
	.menu-image {
		width: 24px;
		height: 24px;
	}

	.grid-item-box {
		flex: 1;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100%;

		.img-box {
			position: relative;

			.tag-box {
				position: absolute;
				z-index: 2;
				top: 0;
				right: 0;
				font-size: 2em;
				line-height: 1;
				padding: 0.4em 0.6em 0.3em;
				transform: scale(0.4) translateX(0.5em) translatey(-0.6em);
				transform-origin: 100% 0;
				border-radius: 200rpx;
				white-space: nowrap;
			}
		}

		.title-box {
			.grid-tip {
				font-size: 24rpx;
				white-space: nowrap;
				text-align: center;
			}
		}
	}
</style>