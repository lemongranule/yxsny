<template>
	<div class="home" id="home">
		<div class="" style="min-height: 45px;line-height: 45px; padding: 5px; border-bottom: 1px solid #ddd" @click="goBack">
			<van-icon name="arrow-left" />
			{{prod.title}}
		</div>
		<div class="" style="padding: 10px;">
			<van-swipe :autoplay="3000">
				<van-swipe-item v-for="(image, index) in prod.cover" :key="index">
					<img :src="image" height="200" />
				</van-swipe-item>
			</van-swipe>

			<div class="" style="padding: 10px;font-size: 14px;">
				<p>{{prod.title}}</p>
				<div class="">
					{{prod.summary}}
				</div>
				<div class="" style="font-size: 20px">
					￥{{prod.price}}
				</div>
			</div>
		</div>

		<div class="" style="padding: 10px;">
			<p>产品详情：暂无</p>
		</div>
		<van-submit-bar :price="prod.price*100" button-text="提交订单" @submit="onSubmit" />

	</div>
</template>
<script>
export default {
	data: function() {
		return {
			images: [
				'https://img.yzcdn.cn/vant/apple-1.jpg',
				'https://img.yzcdn.cn/vant/apple-2.jpg'
			],
			prodId: this.$route.params.id,
			prod: {},

		}
	},
	mounted: function() {
		let vm = this;
		let objs = [{
				'id': '1',
				'title': 'iphonex 维修(换屏)',
				'type': '0',
				'cover': [
					'https://ocdgvcjln.qnssl.com/upload/merchant/prod/db65dbf8-37b8-429b-ab79-6d02e78ed2c5',
					'https://ocdgvcjln.qnssl.com/upload/merchant/prod/70fec022-29fc-47f6-911a-47d74c4e4de7',
					'https://ocdgvcjln.qnssl.com/upload/merchant/prod/e78acfbd-185e-448f-938d-0f36e417cbde'
				],
				'summary': '精修iphonex',
				'price': '399.00'
			},
			{
				'id': '2',
				'title': 'iphone11 维修(换屏)',
				'type': '0',
				'cover': [
					'https://ocdgvcjln.qnssl.com/upload/merchant/prod/db65dbf8-37b8-429b-ab79-6d02e78ed2c5',
					'https://ocdgvcjln.qnssl.com/upload/merchant/prod/70fec022-29fc-47f6-911a-47d74c4e4de7',
					'https://ocdgvcjln.qnssl.com/upload/merchant/prod/e78acfbd-185e-448f-938d-0f36e417cbde'
				],
				'summary': '精修iphone11',
				'price': '499.00'
			},
			{
				'id': '3',
				'title': '配件',
				'type': '1',
				'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/c0f069b0-da8c-45a1-92c8-40506e2641c9'],
				'summary': '质量绝对好的配件',
				'price': '69.00'
			},
			{
				'id': '4',
				'title': '配件',
				'type': '1',
				'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/54d4dd31-3d09-47c4-92cf-f98cb20235de'],
				'summary': '质量绝对好的配件',
				'price': '79.00'
			},
			{
				'id': '5',
				'title': '配件',
				'type': '1',
				'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/9f6f9b7b-68fd-49d9-9012-e59510d01c1e'],
				'summary': '质量绝对好的配件',
				'price': '89.00'
			},
			{
				'id': '6',
				'title': '原厂正品iphonex',
				'type': '2',
				'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/13ea97c9-0e47-4259-a361-ea012a783b55'],
				'summary': '64G 256G',
				'price': '8800.00'
			},
			{
				'id': '7',
				'title': '原厂正品iphone11',
				'type': '2',
				'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/dab318b9-8d0f-4695-9482-664edca9e989'],
				'summary': '64G 256G',
				'price': '7800.00'
			},
			{
				'id': '8',
				'title': '原厂正品iphone11 pro',
				'type': '2',
				'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/ad8f5362-096c-4e34-9171-6d19a536c58b'],
				'summary': '64G 256G',
				'price': '10600.00'
			},
		];
		for (let i = 0; i < objs.length; i++) {
			let obj = objs[i];
			if (obj.id == vm.prodId) {
				vm.prod = obj;
			}
		}
	},
	methods: {
		onSubmit: function() {

		},
		goBack: function() {
			let vm = this;
			vm.$router.push('/')
		}
	}
}

</script>

<style scoped="scoped">

</style>
