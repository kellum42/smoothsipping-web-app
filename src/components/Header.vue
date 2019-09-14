<template>
	<div class="ss-header">
		<img class="ss-header__logo" src="/imgs/ss-logo-full.png" />
        <img @click="menu_button_clicked" class="ss-header__menu-button hover" src="/imgs/icons/1x/menu-icon-black.png" />
        <section style="clear:both"></section>
	</div>
</template>

<script>
	export default {
		methods: {
			menu_button_clicked: function(){
				this.$emit('menu_clicked');
			}
		}
	}
</script>