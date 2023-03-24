<template>
	<div class="menu-right">
		<div class="menu-right_item" :class="{active: item.isActive}" v-for="item in items" @click="changeMenuItem(item)">
			<img :src="item.src" alt="some text" class="icon">
			<div class="text">{{item.text}}</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'MenuRight',
	data: () => ({
		items: [
			{
				text: 'Change amount',
				src: 'img/repeat_icon.svg',
				isActive: false,
			},
			{
				text: 'Change payment method',
				src: 'img/wallet_icon.svg',
				isActive: false,
			},
			{
				text: 'Change date',
				src: 'img/calendar_icon.svg',
				isActive: true,
			},
			{
				text: 'Cancel recurring',
				src: 'img/x-circle_icon.svg',
				isActive: false,
			},
		],
	}),
	methods: {
		// change menu item
		changeMenuItem: function (item) {
			this.items.forEach(el => {
				el.isActive = el === item;
			})
		},
	},
}
</script>