<script lang="ts">
	export let image: string;
    export let alt: string = "...";
	import { scrollRange } from '$lib/actions/change_background_color_linear';
	import { darkMode } from '../../stores/light-dark-mode.store';
</script>

<div class="dynamic-background unselectable">
	<img
		src={image}
		alt={alt}
		use:scrollRange={{
			start: 0,
			end: '100vh',
			property: '--bg-opacity',
			min: $darkMode ? 0.5 : 0.2,
			max: $darkMode ? 0.8 : 0.1
		}}
		use:scrollRange={{
			start: 0,
			end: 'pageHeight',	
			property: '--bg-scale',
			min: 1,
			max: 1.6
		}}
	/>
	<span></span>
</div>

<style>
	:root {
		--bg-opacity: 0.5;
		--bg-scale: 1;
	}

	.dynamic-background {
		position: fixed;
		top: 0;
		width: 100%;
		height: 100lvh;
		z-index: -1;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transform: scale(var(--bg-scale));
        }

        span {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, var(--bg-opacity));
        }
	}
</style>
