<template>
	<view class="uni-container">
		<view class="uni-header-logo">
			<image class="uni-header-image" src="/static/cssIndex.png"></image>
		</view>
		<view class="uni-hello-text">
			<text class="hello-text">uni-app x目前已支持的CSS属性，展示样式仅供参考，文档详见：</text>
			<u-link :href="'https://uniapp.dcloud.io/component/'" :text="'https://uniapp.dcloud.io/component/'" :inWhiteList="true"></u-link>
		</view>
		<view class="uni-panel" v-for="(item, index) in list" :key="item.id">
			<view class="uni-panel-h" :class="item.open ? 'uni-panel-h-on' : ''" @click="triggerCollapse(index, item)">
				<text class="uni-panel-text" :class="item.enable == false ? 'text-disabled' : ''">{{item.name}}</text>
				<image :src="item.pages.length > 0 ? item.open ? arrowUpIcon : arrowDownIcon : arrowRightIcon" class="uni-icon"></image>
			</view>
			<view class="uni-panel-c" v-if="item.open">
				<view class="uni-navigate-item" v-for="(page,key) in item.pages" :key="key" @click="goDetailPage(page)">
					<text class="uni-navigate-text" :class="page.enable == false ? 'text-disabled' : ''">{{page.name}}</text>
					<image :src="arrowRightIcon" class="uni-icon"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script lang="ts">
	type Page = {
		name : string,
		enable ?: boolean,
		url ?: string
	}
	type ListItem = {
		id : string,
		name : string,
		open : boolean,
		pages : Page[],
		url ?: string,
		enable ?: boolean
	}
	export default {
		data() {
			return {
				list: [{
					id: 'background',
					name: 'background',
					open: false,
					pages: [
						{
							name: 'background-color',
							url: '/pages/CSS/background/background-color'
						},
						{
							name: 'background-image',
							url: '/pages/CSS/background/background-image'
						}
					] as Page[]
				}, {
					id: 'border',
					name: 'border',
					open: false,
					pages: [
						{
							name: 'border',
							url: '/pages/CSS/border/border'
						},
						{
							name: 'border-width',
							url: '/pages/CSS/border/border-width'
						},
						{
							name: 'border-style',
							url: '/pages/CSS/border/border-style'
						},
						{
							name: 'border-color',
							url: '/pages/CSS/border/border-color'
						},
						{
							name: 'border-radius',
							url: '/pages/CSS/border/border-radius'
						}
					] as Page[]
				}, {
					id: 'box-shadow',
					name: 'box-shadow',
					open: false,
					pages: [
						{
							name: 'box-shadow',
							url: '/pages/CSS/box-shadow/box-shadow'
						},
					] as Page[]
				}, {
					id: 'flex',
					name: 'flex',
					open: false,
					pages: [
						{
							name: 'align-content',
							url: '/pages/CSS/flex/align-content'
						},
						{
							name: 'align-items',
							url: '/pages/CSS/flex/align-items'
						},
						{
							name: 'flex-basis',
							url: '/pages/CSS/flex/flex-basis'
						},
						{
							name: 'flex-direction',
							url: '/pages/CSS/flex/flex-direction'
						},
						{
							name: 'flex-flow',
							url: '/pages/CSS/flex/flex-flow'
						},
						{
							name: 'flex-grow',
							url: '/pages/CSS/flex/flex-grow'
						},
						{
							name: 'flex-shrink',
							url: '/pages/CSS/flex/flex-shrink'
						},
						{
							name: 'flex',
							url: '/pages/CSS/flex/flex'
						},
						{
							name: 'justify-content',
							url: '/pages/CSS/flex/justify-content'
						}
					] as Page[]
				}, {
					id: 'layout',
					name: 'layout',
					open: false,
					pages: [
						{
							name: 'height',
							url: './layout/height/height'
						},
						{
							name: 'max-height',
							url: '/pages/CSS/layout/max-height'
						},
						{
							name: 'max-width',
							url: '/pages/CSS/layout/max-width'
						},
						{
							name: 'min-height',
							url: '/pages/CSS/layout/min-height'
						},
						{
							name: 'min-width',
							url: '/pages/CSS/layout/min-width'
						},
						{
							name: 'position',
							url: '/pages/CSS/layout/position'
						},
						{
							name: 'width',
							url: '/pages/CSS/layout/width'
						}
					] as Page[]
				}, {
					id: 'margin',
					name: 'margin',
					open: false,
					pages: [
						{
							name: 'margin-bottom',
							url: '/pages/CSS/margin/margin-bottom'
						},
						{
							name: 'margin-left',
							url: '/pages/CSS/margin/margin-left'
						},
						{
							name: 'margin-right',
							url: '/pages/CSS/margin/margin-right'
						},
						{
							name: 'margin-top',
							url: '/pages/CSS/margin/margin-top'
						}, {
							name: 'margin',
							url: '/pages/CSS/margin/margin'
						}
					] as Page[]
				}, {
					id: 'padding',
					name: 'padding',
					open: false,
					pages: [
						{
							name: 'padding-bottom',
							url: '/pages/CSS/padding/padding-bottom'
						},
						{
							name: 'padding-left',
							url: '/pages/CSS/padding/padding-left'
						},
						{
							name: 'padding-right',
							url: '/pages/CSS/padding/padding-right'
						},
						{
							name: 'padding-top',
							url: '/pages/CSS/padding/padding-top'
						}, {
							name: 'padding',
							url: '/pages/CSS/padding/padding'
						}
					] as Page[]
				}, {
					id: 'text',
					name: 'text',
					open: false,
					pages: [
						{
							name: 'color',
							url: '/pages/CSS/text/color'
						},
						{
							name: 'font-family',
							url: '/pages/CSS/text/font-family'
						},
						{
							name: 'font-size',
							url: '/pages/CSS/text/font-size'
						},
						{
							name: 'font-style',
							url: '/pages/CSS/text/font-style'
						},
						{
							name: 'font-weight',
							url: '/pages/CSS/text/font-weight'
						},
						{
							name: 'line-height',
							url: '/pages/CSS/text/line-height'
						},
						{
							name: 'text-align',
							url: '/pages/CSS/text/text-align'
						},
						{
							name: 'text-decoration-line',
							url: '/pages/CSS/text/text-decoration-line'
						}
					] as Page[]
				}, {
					id: 'animate',
					name: '动画',
					open: false,
					pages: [
						{
							name: 'transition',
							url: '/pages/CSS/transition/transition'
						},
						{
							name: 'transform',
							url: '/pages/CSS/transform/transform'
						}
					] as Page[]
				}
				] as ListItem[],
				arrowUpIcon: '/static/icons/arrow-up.png',
				arrowDownIcon: '/static/icons/arrow-down.png',
				arrowRightIcon: '/static/icons/arrow-right.png',
			}
		},
		methods: {
			triggerCollapse(index ?: number, item : ListItem) {
				if (item.pages.length == 0) {
					const page : Page = {
						name: item.name,
						enable: item.enable,
						url: item.url
					}
					this.goDetailPage(page);
					return;
				}
				for (var i = 0; i < this.list.length; ++i) {
					if (index == i) {
						this.list[i].open = !this.list[i].open;
					} else {
						this.list[i].open = false;
					}
				}
			},
			goDetailPage(e : Page) {
				if (e.enable == false) {
					uni.showToast({
						icon: 'none',
						title: '暂不支持'
					})
					return
				}
				const url = e.url != null ? e.url! : `/pages/CSS/${e.name}/${e.name}`
				uni.navigateTo({
					url
				})
			}
		}
	}
</script>

<style>
	@import '../../common/uni-uvue.css';
</style>