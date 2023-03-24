<template>
	<header>
		<div class="header-inner">
			<div class="header-inner_top">
				<h1>Donations</h1>
			</div>
			<div class="header-inner_bottom">
				<div class="search">
					<input type="search" class="search__box" placeholder="Search">
					<label for="search" class="search__icon-block">
						<svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path d="M8.25 14.25C11.5637 14.25 14.25 11.5637 14.25 8.25C14.25 4.93629 11.5637 2.25 8.25 2.25C4.93629 2.25 2.25 4.93629 2.25 8.25C2.25 11.5637 4.93629 14.25 8.25 14.25Z" stroke="#6C6D6F" stroke-linecap="round" stroke-linejoin="round"/>
							<path d="M15.7499 15.7499L12.4874 12.4874" stroke="#6C6D6F" stroke-linecap="round" stroke-linejoin="round"/>
						</svg>
					</label>
				</div>
				<div class="select">
					<input class="select__input" type="hidden" name="">
					<div class="select__head" @click="changeOptionsList">{{chosenItem}}</div>
					<ul class="select__list" v-show="statusSelect">
						<li class="select__item" v-for="item in listItems" @click="changeOptionsItem(item.text)">{{item.text}}</li>
					</ul>
				</div>
			</div>
		</div>
	</header>
</template>

<script>
export default {
	name: 'Header',
	data: () => ({
		statusSelect: false,
		chosenItem: 'All statuses',
		listItems: [
			{
				text: 'All statuses',
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
		// open and close All statuses list
			changeOptionsList: function () {
				this.statusSelect ? this.statusSelect = false : this.statusSelect = true;
			},
			// change chosen list item in select
			changeOptionsItem: function (name) {
				this.chosenItem = name;
				this.changeOptionsList();
			},
		},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>