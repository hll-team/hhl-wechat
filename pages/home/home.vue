<template>
	<view class="index">
		<hll-header style="position: absolute;"></hll-header>
		<view class="index-header">
			<AdvertSwiper></AdvertSwiper>
			<view class="vip-code" @click="showVipCode = true">
				<image style="height:51px;width:51px;" src="/static/img/home/vip-icon.png"></image>
				<view>会员码</view>
			</view>
			<view class="big-logo">
				<image style="height:70px;width:348px;" src="/static/img/logo-big-white.png"></image>
			</view>
		</view>
		<view class="flex justify-around" style="margin-top:8px;">
			<HllCard style="flex:0.45" :cardData="cardData[0]"/>
			<view style="border-right:1px solid #000;"></view>
			<HllCard style="flex:0.45" :cardData="cardData[1]"/>
		</view>
		<hll-title :info="titleInfo"></hll-title>
		<view>
			<swiper class="shop-swiper" style="height: 210px;width:100%;" :indicator-dots="false" :autoplay="true" interval="3000" duration="1000">
				<swiper-item v-for="item in shopsList" :key="item.id">
					<view class="swiper-item">
						<view class="swiper-item-desc">
							<view class="text-bold">{{item.name}}</view>
							<view class="text-sm">{{item.desc}}</view>
						</view>
						<image style="height: 210px;width:100%;" :src="item.img"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		
		<VipCode :showModal.sync="showVipCode"></VipCode>
	</view>
</template>

<script>
	import HllCard from '@/components/hll-card.vue'
	import AdvertSwiper from './components/advert-swiper.vue'
	import VipCode from './components/vip-code.vue'
	export default {
		components:{
			HllCard,
			AdvertSwiper,
			VipCode,
		},
		data() {
			return {
				showVipCode:  false,
				cardData:[{enName:'COUPON\nCENTER',cnName:'领劵中心',num:15,url: '/subPackages/home/coupon-center/coupon-center'},
				{enName:'GIFT\nCARD',cnName:'礼品卡',num:12,icon: '/static/img/home/gift-card.png'}],
				shopsList:[
					{id:1,name:'阿华田爆浆球',desc:'真的很好吃，赶快买它',img:'/static/img/HLL 08 04.png'},
					{id:2,name:'好吃的',desc:'真的很好吃，赶快买它',img:'/static/img/HLL 08 04.png'},
					{id:3,name:'吃不吃',desc:'真的很好吃，赶快买它',img:'/static/img/HLL 08 04.png'},
					{id:4,name:'快来吃',desc:'真的很好吃，赶快买它',img:'/static/img/HLL 08 04.png'}
				],
				titleInfo:{
					enName: 'NEWS.',
					cnName: '品牌动向',
					url: ''
				}
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="less">
.index {
	background: #E6DEDB;
	.index-header{
		position: relative;
		.vip-code{
			position: absolute;
			right: 10px;
			bottom: 120px;
			color: #FFFFFF;
			font-size: 16px;
		}
		.big-logo{
			position: absolute;
			bottom: 21px;
			left:50%;
			transform: translateX(-50%);
		}
	}
	.shop-swiper{
		.swiper-item{
			.swiper-item-desc{
				position: absolute;
				z-index: 999;
				bottom: 15px;
				color: #FFFFFF;
				left: 15px;
			}
		}
	}
}
</style>
