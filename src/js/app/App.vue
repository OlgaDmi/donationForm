<template>
  <div id="app-inner" class="app-inner">
	  <Header/>
	  <div class="content">
		  <div class="content__inner_left">
			  <DonationsBlock/>
			  <Transactions/>
		  </div>
		  <div class="content__inner_right">
			  <MenuRight/>
		  </div>
	  </div>
  </div>
</template>

<script>
import Transactions from './components/Transactions.vue'
import DonationsBlock from './components/DonationsBlock.vue'
import Header from './components/Header.vue'
import MenuRight from './components/MenuRight.vue'
export default {
  name: 'App',
	components: {
		Transactions,
		DonationsBlock,
		Header,
		MenuRight,
	},
}
</script>