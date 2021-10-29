<template>
	<div class="app">
		<LayoutWidget position="top">
			<WidgetsDock/>
		</LayoutWidget>

		<div class="main-wrapper">
			<LayoutWidget position="left" align="center">
				<WidgetsDock/>
			</LayoutWidget>

			<main>
				<Nuxt/>
			</main>

			<LayoutWidget position="right">
				<WidgetsDock/>
			</LayoutWidget>
		</div>

		<LayoutWidget position="bottom">
			<WidgetsDock/>
		</LayoutWidget>

	</div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.app {
	background-color: $dark;
	height: 100vh;
	display: flex;
	flex-flow: column;
	overflow: hidden;
}

.main-wrapper {
	padding: $margin;
	width: 100%;
	height: 100%;
	display: flex;
}

main {
	border-radius: $radius;
	background-color: $light;
	background-image: url("~assets/images/bg.jpg");
	background-size: cover;
	padding: $margin;
	height: 100%;
	width: 100%;
}

</style>
