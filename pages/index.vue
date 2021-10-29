<template>
	<div class="container">
		<div class="dummy">
			<div class="content">
				<h3>Task Manager</h3>
				<div class="flex">
					<div></div>
					<div></div>
					<div></div>
				</div>
			</div>
		</div>

	</div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.dummy {
	width: 300px;
	height: 300px;
	padding: $margin;
	position: relative;
}

.dummy:before {
	background: #53e6e6;
	mix-blend-mode: difference;
	position: absolute;
	inset: 0;
	content: '';
	border-radius: $radius;
	z-index: 1;
}

.flex {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-top: 40px;
	z-index: 2;
}

.flex > div {
	width: 32%;
	height: 100px;
	background: seagreen;
	border-radius: $radius;
}

.content {
	color: white;
	position: relative;
	z-index: 2;
}
</style>
