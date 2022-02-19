<template>
	<view>
		<uni-list>
			<uni-list-item title="列表右侧显示角标" :show-badge="true" badge-text="12" showArrow="true" :clickable="true"></uni-list-item>
			<uni-list-item title="列表左侧带略缩图" note="列表描述信息" link to="detail"
				thumb="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png"
				thumb-size="lg" rightText="右侧文字"></uni-list-item>
			<uni-list-item :show-extra-icon="true" :extra-icon="extraIcon1" title="列表左侧带扩展图标"></uni-list-item>
			<uni-list-chat v-for="(item,index) in list" 
				:avatar-circle="index % 4 ? true : false" 
				:title="item.title" 
				:avatar="item.avatar"
				 to="detail"
				:note="item.note" 
				time="2020-02-02 20:20"
				badge-positon="left"
				link
				:badge-text="index === '1' ? 'dot' : index"
				></uni-list-chat>
			<!-- 头像显示圆点 -->
			<uni-list-chat title="uni-app"
				avatar="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png"
				note="您收到一条新的消息" time="2020-02-02 20:20" badge-positon="left" badge-text="dot"></uni-list-chat>
			<!-- 头像显示角标 -->
			<uni-list-chat title="uni-app" :clickable="true"
				avatar="https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png"
				note="您收到一条新的消息" time="2020-02-02 20:20" badge-positon="left" badge-text="99"></uni-list-chat>
				<!-- 垂直排列，无略缩图，主标题+副标题显示 -->
				    </uni-list>
		<uni-load-more status="more"></uni-load-more>
		
	</view>
</template>

<script>
	export default {
		data() {
			const list = []
			for (var i = 0; i < 10; i++) {
				list.push({
					avatar: "https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dc-site/460d46d0-4fcc-11eb-8ff1-d5dcf8779628.png",
					title: `uni-app${i}`,
					note: '您收到一条新的消息' + i
				})
			}
			return {
				extraIcon1: {
					color: '#4cd964',
					size: '22',
					type: 'spinner'
				},
				list:list,
				isLoadMore: false,
				loadCount:0
			}
		},
		created() {
			console.log(uni.$u);
		},
		methods: {
			onPullDownRefresh(){
				uni.showToast({
					title:"刷新成功",
					icon: 'none'
				})
				uni.stopPullDownRefresh()
				console.log('refresh')
			},
			onReachBottom(){  //上拉触底函数
				
				if(!this.isLoadMore){  //此处判断，上锁，防止重复请求
					this.loadCount++
					this.isLoadMore=true
					if(this.loadCount === 5){
						this.isLoadMore = 'noMore'
					}
					let len = 5 ,index = 0
					for (let i = index; i < len.length; i++) {
						Things[i]
					}
					
					console.log('loadMore')
					
				}
			},
		}
	}
</script>

<style>
</style>
