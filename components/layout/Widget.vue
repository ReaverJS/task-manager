<template>
	<div class="widget" ref="widget" :class="`${position} ${opened ? 'opened' : ''}`">
		<div class="content-wrapper" ref="contentWrapper" :class="align">
			<div class="dummy" style="width: 300px">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias aliquid assumenda autem consequuntur
				fuga nisi numquam odio possimus, quibusdam soluta!
			</div>
		</div>
		<button @click="test">asd</button>
	</div>
</template>

<script>
import globalStyles from '@/assets/styles/global.scss'

export default {
	props: {
		position: {
			type: String,
			required: true
		},
		align: {
			type: String,
			default: 'center'
		}
	},
	data: () => {
		return {
			opened: true
		}
	},
	mounted() {
		setTimeout(this.resize, 100)
		window.addEventListener("resize", this.resize)
	},
	destroyed() {
		window.removeEventListener("resize", this.resize)
	},
	methods: {
		resize() {
			if (this.position === 'top' || this.position === 'bottom') this.setHeight()
			else this.setWidth()
		},
		setWidth() {
			const widget = this.$refs.widget
			if (this.opened) {
				const wrapper = this.$refs.contentWrapper
				const width = wrapper.getBoundingClientRect().width
				const margin = parseInt(globalStyles.margin)

				widget.style.minWidth = `${width + margin}px`
			} else {
				widget.style.minWidth = `0px`
			}
		},
		setHeight() {
			const widget = this.$refs.widget
			if (this.opened) {
				const wrapper = this.$refs.contentWrapper
				const height = wrapper.getBoundingClientRect().height
				const margin = parseInt(globalStyles.margin)

				widget.style.minHeight = `${height + margin}px`
			} else {
				widget.style.minHeight = `0px`
			}
		},
		test() {
			console.log(globalStyles)
			this.opened = !this.opened
			this.resize()
		}
	}
}
</script>

<style scoped lang="scss">

.widget {
	position: relative;
	min-width: 0;
	min-height: 0;

	transition-property: min-height, min-width, margin-left, margin-right;
	transition-duration: 1s;

	.content-wrapper {
		position: absolute;
		display: flex;

		transition-property: right, left;
		transition-duration: 1s;

		&.center {
			justify-content: center;
			align-items: center;
		}

		&.end {
			justify-content: flex-end;
			align-items: flex-end;
		}

		&.start {
			justify-content: flex-start;
			align-items: flex-start;
		}
	}
}

.left {
	margin-right: 0;

	.content-wrapper {
		right: $margin;
		height: 100%;
	}
}

.right {
	margin-left: 0;

	.content-wrapper {
		left: $margin;
		height: 100%;
	}
}

.top {
	margin: 0 $margin;
	.content-wrapper {
		bottom: 0;
		width: 100%;
	}
}

.bottom {
	margin: 0 $margin;
	.content-wrapper {
		top: 0;
		width: 100%;
	}
}




.dummy {
	padding: $margin;
	background-color: $light;
	border-radius: $radius;
}

button {
	position: fixed;
	right: 50px;
	z-index: 99;
}

.left {
	button {
		top: 50px;
	}
}

.right {
	button {
		top: 80px;
	}
}

.top {
	button {
		top: 110px;
	}
}

.bottom {
	button {
		top: 140px;
	}
}

</style>
