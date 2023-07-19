<template>
	<view>
		222
	</view>
</template>

<script lang="ts" setup>
	import { LwuXHR, RequestConfig } from 'lwu-xhr';
	console.log(LwuXHR);
	// 创建实例
	const xhr = LwuXHR.create({
		baseURL: 'https://api.kags.cn',
		// headers: {
		// 	'content-type': 'application/json',
		// 	a: 1
		// },
		timeout: 0
	})
	
	// 请求拦截
	xhr.interceptors.request.use((config) => {
		// config.headers = {
		// 	...config.headers,
		// 	b: 2
		// }
		//  请求前追加参数
		config.params = {
			c: 3
		}
		return config;
	}, (error) => {
		console.log(error);
		return Promise.reject(error);
	}, xhr);
	
	// 响应拦截
	xhr.interceptors.response.use((response) => {
		// 可以随意修改响应数据
		response['code'] = 2;
		return response;
	});
	
	xhr
		.setConfig({
			params: {
				a: 1,
				b: 2,
				...xhr.getConfig().params
			},
			data: {
				c: 1
			}
			// dataType: 'string'
		} as RequestConfig)
		.get('/v1/home/siteinfo')
		.then(res => {
			console.log(res);
		})
		.catch(err => {
			console.log(err);
		})
		
	// xhr
	// 	.get('/v1/home/siteinfo')
	// 	.then(res => {
	// 		console.log(res);
	// 	})
	// 	.catch(err => {
	// 		console.log(err);
	// 	})
</script>

<style>

</style>
