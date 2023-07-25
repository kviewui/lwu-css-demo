<template>
	<view>
		222
	</view>
</template>

<script lang="ts" setup>
	import { create, RequestConfig, IInterceptorDecorator } from 'lwu-xhr';
	const request = create({
		useInterceptor: true
	}) as IInterceptorDecorator;
	
	console.log(request);
	
	// 请求拦截
	request.setRequestInterceptor((config: RequestConfig) => {
		console.log(config);
		config.baseURL = 'https://api.kags.cn';
		return config;
	})
	
	// 响应拦截
	request.setResponseInterceptor((response) => {
		console.log(response);
		return response;
	})
	
	// 超时处理
	// request.timeout(10, () => {
	// 	console.log('请求超时了');
	// })
	
	function Test1() {
		return request
				.timeout(10, () => {
					console.log('请求超时了啊');
				})
				.get('/v1/home/siteinfo', {
					baseURL: 'https://api.kags.cn'
				})
	}
	
	function Test2() {
		return request
				.get('/v1/home/siteinfo', {
					baseURL: 'https://api.kags.cn'
				})
	}
	
	Promise.all([Test1(), Test2()])
		.then((result) => {
			console.log(result);
		})
	
	// request
	// 	.timeout(10, () => {
	// 		console.log('请求超时了啊');
	// 	})
	// 	.get('/v1/home/siteinfo', {
	// 		baseURL: 'https://api.kags.cn'
	// 	})
	// 	.then((res) => {
	// 		console.log(typeof res);
	// 	})
	// 	.catch((err) => {
	// 		console.log(err);
	// 	})
		
	// request
	// 	.get('/v1/home/siteinfo', {
	// 		baseURL: 'https://api.kags.cn'
	// 	})
	// 	.then((res) => {
	// 		console.log(typeof res);
	// 	})
	// 	.catch((err) => {
	// 		console.log(err);
	// 	})
</script>

<style>

</style>
