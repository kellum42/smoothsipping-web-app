<template>
	<div id="app" :class="{ sidebar_visible: sidebar_open }">
		<Sidebar :user="current_user" @menu_clicked="toggle_sidebar" />
		<div @click="toggle_sidebar" class="ss-overlay"></div>
		<div class="ss-content">
			<Header @menu_clicked="toggle_sidebar" />
			<router-view />
		</div>
	</div>
</template>

<!-- TODO: Make api call in mounted -->
<!-- Testing branch capabilities -->
<script>
import Sidebar from "@/components/Sidebar.vue";
import Header from "@/components/Header.vue";

export default {
	name: "app",
	components: {
		Sidebar,
		Header
	},
	data() {
		return {
			sidebar_open: false,
			current_user: {
				name: "Alicia Keys",
				points: 348,
				member_since: "5/3/19",
				level: 2,
				avatar: "/imgs/user_avatar.png"
			},
			checked_in_location: {}
		};
	},
	methods: {
		toggle_sidebar: function() {
			this.sidebar_open = !this.sidebar_open;
		}
	}
};
</script>
