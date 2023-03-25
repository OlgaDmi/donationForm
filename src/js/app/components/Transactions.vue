<template>
	<div class="transactions">
		<div class="transactions-head">
			<div class="tabs">
				<div class="tabs-item" :class="{active: item.isActive}" v-for="item in tabs" @click="changeTab(item)">{{item.text}}</div>
			</div>
		</div>
		<div class="transactions-inner">
			<div v-if="currentTab == 'Behavior'">
				<div class="line line__des">
					<div class="label">Designation</div>
					<div class="select">
						<input class="select__input" type="hidden" name="">
						<div class="select__head" @click="changeSelectStatus('checkout')">{{ currCheckout }}</div>
						<ul class="select__list" v-show="checkoutStatus">
							<li class="select__item" v-for="item in checkoutList" @click="changeCheckoutItem(item.text)">{{ item.text }}</li>
						</ul>
					</div>
				</div>
				<div class="line line__goal">
					<div class="label">Goal</div>
					<input type="text" class="input-txt">
					<div class="select">
						<input class="select__input" type="hidden" name="">
						<div class="select__head" @click="changeSelectStatus('usd')">{{ currUsd }}</div>
						<ul class="select__list" v-show="checkoutUsd">
							<li class="select__item" v-for="item in usdList" @click="changeUsdItem(item.text)">{{ item.text }}</li>
						</ul>
					</div>
				</div>
				<div class="line line_amount">
					<div class="label">Default Amount</div>
					<div class="line_amount_right">
						<div class="radio-box">
							<div class="radio-box__item">
								<input id="radio-1" type="radio" name="radio" value="1">
								<label for="radio-1">Match Checkout Setting</label>
							</div>
							<div class="radio-box__item">
								<input id="radio-2" type="radio" name="radio" value="2" checked>
								<label for="radio-2">Customize</label>
							</div>
						</div>
						<div class="checkbox-box">
							<input type="checkbox" class="custom-checkbox" id="currency" name="currency">
							<label for="currency">Allow donor to change default currency</label>
						</div>
					</div>
				</div>
				<div class="line line_border-size">
					<div class="label">Border size</div>
					<div class="rangeslider">
						<div class="rangeslider-box">
							<Slider :tooltips="false" :min="0" :max="4" v-model="rangeValueBorderSize" />
						</div>
						<div class="rangeslider__num" v-text="rangeValueBorderSize+'px'"></div>
					</div>
				</div>
				<div class="line line_border-radius">
					<div class="label">Border radius</div>
					<div class="rangeslider">
						<div class="rangeslider-box">
							<Slider :min="0" :max="20" :tooltips="false" v-model="rangeValueBorderRadius" />
						</div>
						<div class="rangeslider__num" v-text="rangeValueBorderRadius+'px'"></div>
					</div>
				</div>
			</div>
			<div v-if="currentTab == 'Appearance'">
				<div class="line line__des">
					content Appearance
				</div>
			</div>
			<div v-if="currentTab == 'Custom Fields'">
				<div class="line line__des">
					content Custom Fields
				</div>
			</div>
			<div v-if="currentTab == 'Questions'">
				<div class="line line__des">
					content Questions
				</div>
			</div>
			<div v-if="currentTab == 'URL Control'">
				<div class="line line__des">
					content URL Control
				</div>
			</div>
		</div>
		<div class="transactions-bottom">
			<button class="btn btn_green">Save changes</button>
			<button class="btn btn_white">Cancel</button>
		</div>
	</div>
</template>

<style src="@vueform/slider/themes/default.css"></style>
<script>
import Slider from '@vueform/slider'

export default {
	name: 'Transactions',
	data: () => ({
		rangeValueBorderSize: 2,
		rangeValueBorderRadius: 15,
		checkoutStatus: false,
		currCheckout: 'Match Checkout Setting',
		checkoutUsd: false,
		currUsd: 'USD',
		currentTab: 'Behavior',
			tabs: [
				{
					text: 'Behavior',
					isActive: true,
				},
				{
					text: 'Appearance',
					isActive: false,
				},
				{
					text: 'Custom Fields',
					isActive: false,
				},
				{
					text: 'Questions',
					isActive: false,
				},
				{
					text: 'URL Control',
					isActive: false,
				},
			],
			usdList: [
				{
					text: 'USD',
				},
				{
					text: '111',
				},
				{
					text: '222',
				},
				{
					text: '333',
				},
			],
		checkoutList: [
			{
				text: 'Match Checkout Setting',
			},
			{
				text: 'Grapes',
			},
			{
				text: 'Oranges',
			},
			{
				text: 'Apples',
			},
		],
	}),
	methods: {
		// open and close select list
		changeSelectStatus: function (name) {
			switch (name) {
				case 'checkout':
					this.checkoutStatus ? this.checkoutStatus = false : this.checkoutStatus = true;
					break;
				case 'usd':
					this.checkoutUsd ? this.checkoutUsd = false : this.checkoutUsd = true;
					break;
			}
		},
		// change chosen list item in usd
		changeUsdItem: function (name) {
			this.currUsd = name;
			this.changeSelectStatus('usd');
		},
		// change chosen list item in usd
		changeCheckoutItem: function (name) {
			this.currCheckout = name;
			this.changeSelectStatus('checkout');
		},
		// change tabs function
		changeTab: function (tab) {
				this.tabs.forEach(el => {
					el.isActive = el === tab;
				})
				this.currentTab = tab.text;
			},
	},
	components: {
			Slider,
	},
}

</script>
