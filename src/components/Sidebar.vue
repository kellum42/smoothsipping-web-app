<template>
	<div class="ss-sidebar">
		<img
			@click="menu_button_clicked"
			class="ss-sidebar__menu-button hover"
			src="/imgs/icons/1x/menu-icon-white.png"
		/>
		<div style="text-align:left">
			<img class="ss-sidebar__logo" src="/imgs/ss-logo-full.png" />
		</div>

		<div class="ss-sidebar__user-section">
			<p class="ss-sidebar__username">{{ user.name }}</p>
			<div
				:style="{ backgroundImage: 'url(' + user_avatar + ')' }"
				class="ss-sidebar__user-avatar"
			></div>
			<h1
				style="font-size: 46px;margin:0"
				class="ss-sidebar__user-points"
			>
				{{ user.points }}
			</h1>
			<p class="ss-sidebar__user-level">{{ user_level }}</p>
			<p class="ss-sidebar__user-joined">{{ user_joined }}</p>
		</div>

		<div class="ss-sidebar__menu">
			<a class="ss-sidebar__menu-item" href="/">Home</a>
			<a class="ss-sidebar__menu-item" href="/">Earn Points</a>
			<a class="ss-sidebar__menu-item" href="/">Redeem Points</a>
			<a class="ss-sidebar__menu-item" href="/">My Rewards</a>
			<a class="ss-sidebar__menu-item" href="/">Partner Breweries</a>
			<a class="ss-sidebar__menu-item" href="/">My Account</a>
		</div>
	</div>
</template>

<script>
import { globals } from "../globals.js";

export default {
	data() {
		return {
			user: globals.current_user
		};
	},
	methods: {
		menu_button_clicked: function() {
			this.$emit("menu_clicked");
		}
	},
	computed: {
		user_avatar: function() {
			return this.user.avatar || "some placeholder";
		},
		user_joined: function() {
			if (!this.user.member_since) {
				return "";
			}
			return "Member Since: " + this.user.member_since;
		},
		user_level: function() {
			var level = this.user.level || 0;
			return "Level " + level + " Member";
		}
	}
};
</script>
