<template>
	<div id="app" :class="{ sidebar_visible: globals.sidebar_open }">
		<Sidebar @menu_clicked="toggle_sidebar" />
		<div @click="toggle_sidebar" class="ss-overlay"></div>
		<div class="ss-content">
			<Header @menu_clicked="toggle_sidebar" />
			<router-view />
		</div>
	</div>
</template>

<!-- TODO: Make api call in mounted -->
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
			globals: {
				sidebar_open: false,
				current_user: {
					name: "Alicia Keys",
					points: 348,
					member_since: "5/3/19",
					level: 2,
					avatar: "/imgs/user_avatar.png"
				},
				checked_in_location: {}
			}
		};
	},
	methods: {
		toggle_sidebar: function() {
			this.globals.sidebar_open = !this.globals.sidebar_open;
		}
	}
};
</script>
