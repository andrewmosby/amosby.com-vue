<template>
	<header role="banner" class="header">
		<!-- <div>
			<a class="siteLogo" @click="changePage('home')">
				<i class="icon-material siteLogo_icon">brightness_auto</i> Andrew Mosby
			</a>
			<h2>{{ headerStory.title }}</h2>
			<p v-html="headerStory.copy"></p>
			<cite>~ {{ headerStory.author }}</cite>
		</div> -->
		<nav class="header_nav">
			<a v-for="navItem in navItems" @click="changePage(navItem.pageName)" class="header_nav_link">
				<i class="icon-material header_nav_icon">{{ navItem.icon }}</i>
				<span class="header_nav_text">{{ navItem.text }}</span>
			</a>
		</nav>
	</header>
</template>

<script>
	export default {
		data: function () {
			return {
				navItems: [
					{
						pageName: 'home',
						text: 'Home',
						icon: 'home'
					},
					{
						pageName: 'projects',
						text: 'Projects',
						icon: 'code'
					},
					{
						pageName: 'resume',
						text: 'Résumé',
						icon: 'work'
					},
					{
						pageName: 'philosophies',
						text: 'Philosophies',
						icon: 'format_quote'
					},
					{
						pageName: 'about',
						text: 'About',
						icon: 'person'
					}
				],
				headerStory: {
					title: 'Cover Letter',
					copy: '<p>Duis suscipit nibh et libero vestibulum faucibus. Vivamus ullamcorper sodales rhoncus. Maecenas consequat sagittis arcu in aliquam. Interdum et malesuada fames ac ante ipsum primis in faucibus.</p><p>Duis suscipit nibh et libero vestibulum faucibus. Vivamus ullamcorper sodales rhoncus. Maecenas consequat sagittis arcu in aliquam. Interdum et malesuada fames ac ante ipsum primis in faucibus.</p>',
					author: 'Andrew Mosby'
				}
			};
		},
		methods: {
			changePage: function (pageName) {
				this.$emit('emitChangePage', pageName)
			}
		},
	}
</script>

<style lang="scss">
	@import "../variables.scss";

	$headerbg: $colorYellow;
	$headerColor: $colorDarkGray;

	.header {
		position: fixed;
		top: 0;
		left: 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 100vh;
		width: 56px;
		padding: 16px;
		background: $headerbg;
		color: white;
		transition: $transition;
		overflow: hidden;
	    z-index: 100;

    	&:hover {
			width: 140px;
			.header_nav_text {
				display: block;
			}
		}
	}
	@media (hover: none) { 
		.header {
			width: 140px;
			.header_nav_text {
				display: block;
			}
		}
		@media (min-width: $tabletMin) {
			main {
				padding-left: 188px; //header width + padding-left of main
			}
		}

	}
	.header_nav_link {
		display: flex;
		padding-left: 0;
		cursor: pointer;
		font-family: $fontPrimary;
		font-weight: 400;
		text-decoration: none;
		color: $headerColor;
		font-size: 13px;
		align-items: center;
		transition: $transition;
		user-select: none;

		&:hover {
			padding-left: 8px;
			text-decoration: none;
			color: $colorBlue;
		}

		+ .header_nav_link {
			margin-top: 20px;
		}
	}
	.header_nav_text {
		display: none;
	    padding-left: 8px;
	}
	// .siteLogo {
	// 	display: flex;
	// 	align-items: center;
	// 	margin-bottom: 16px;
	// 	padding-left: 0;
	// 	text-decoration: none;
	// 	cursor: pointer;
	// 	font-family: $fontSecondary;
	// 	font-size: 22px;
	// 	color: white;

	// 	&:hover {
	// 		padding-left: 10px;
	// 		color: lighten($colorBlue, 35%);
	// 		text-decoration: none;
	// 	}
	// }
	.siteLogo_icon {
		font-size: 40px;
		margin-right: 12px;
	}
	@media (max-width: $phoneMax) {
		.header {
			height: auto;
			width: 100%;
			top: inherit;
			bottom: 0;

			&:hover {
				width: 100%;
			}
		}
		.header_nav {
			display: flex;
			justify-content: center;
			width: 100%;
		}
		.header_nav_link {
			display: block;
			text-align: center;

			+ .header_nav_link {
				margin-top: 0;
				margin-left: 12px;
			}
			&:hover {
				padding-left: 0;
			}
		}
		.header_nav_icon {
			display: block;
		}
		.header_nav_text {
			display: block !important;
			padding-left: 0;
		}
	}
</style>