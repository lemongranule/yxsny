<template>
	<div class="home" id="home">
		<div class="" style="min-height: 45px;line-height: 45px; text-align: center; padding: 5px; border-bottom: 1px solid #ddd">
			修一修手机维修
		</div>
		<div class="" style=" position: absolute;">
			<van-sidebar v-model="activeKey" @change="sideBarChange">
				<van-sidebar-item title="维修" />
				<van-sidebar-item title="配件" />
				<van-sidebar-item title="手机" />
			</van-sidebar>
		</div>
		<div class="contents">
			<div class="prod-content">
				<van-row gutter="20">
					<van-col span="12" v-for="(item,index) in prods" :key="index" v-if="item.type==activeKey">
						<div class="" style="margin:10px 0;" @click="toDetails(item.id)">
							<div class="" style="max-height: 100px;overflow:hidden;">
								<van-image fit="cover" :src="item.cover[0]" />
							</div>
							<div class="prod-info" style="font-size: 13px;">
								<div class="prod-title">
									{{item.title}}
								</div>
								<div class="prod-summary" style="color: rgb(221, 221, 221);font-size: 12px">
									{{item.summary}}
								</div>
								￥{{item.price}}
							</div>
						</div>
					</van-col>
				</van-row>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	data: function() {
		return {
			activeKey: 0,
			prods: [],
			fetching: false,

			homeStyle: {},

			count: 0,
			isLoading: false,
		}
	},
	mounted: function() {
		let vm = this;
		vm.onRefresh();
		let width = window.innerWidth;
		let height = window.innerHeight;
		vm.homeStyle = {
			'height': height,
		}

	},
	methods: {
		sideBarChange: function(index) {
			let vm = this;
			vm.prods = [];
			vm.onRefresh();
		},
		onRefresh() {
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
					'price': '29.00-129.00'
				},
				{
					'id': '4',
					'title': '配件',
					'type': '1',
					'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/54d4dd31-3d09-47c4-92cf-f98cb20235de'],
					'summary': '质量绝对好的配件',
					'price': '10.00-59.00'
				},
				{
					'id': '5',
					'title': '配件',
					'type': '1',
					'cover': ['https://ocdgvcjln.qnssl.com/upload/merchant/prod/9f6f9b7b-68fd-49d9-9012-e59510d01c1e'],
					'summary': '质量绝对好的配件',
					'price': '59.00-89.00'
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
			setTimeout(() => {
				for (let i = 0; i < objs.length; i++) {
					let obj = objs[i];
					vm.prods.push(obj);
				}
				this.$toast('刷新成功');
				this.isLoading = false;
				this.count++;
			}, 1000)
		},
		toDetails: function(prodId) {
			let vm = this;
			vm.$router.push({ path: `/item/${prodId}` });
		}
	}
}

</script>

<style scoped="scoped">
.contents {
	margin-left: 85px;
	padding: 10px;
}

.prod-title {
	min-height: 44px;
	word-wrap: break-word
}

.prod-info {
	padding: 0 5px;
}

</style>
