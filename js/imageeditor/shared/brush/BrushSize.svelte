<script lang="ts">
	import { click_outside } from "../utils/events";
	import { createEventDispatcher } from "svelte";
	import { BrushSize } from "@gradio/icons";

	export let selected_size: number;
	export let min: number;
	export let max: number;

	const dispatch = createEventDispatcher<{
		click_outside: void;
	}>();
</script>

<div class="wrap" use:click_outside={() => dispatch("click_outside")}>
	<span>
		<BrushSize />
	</span>
	<input type="range" bind:value={selected_size} {min} {max} step={1} />
</div>

<style>
	.wrap {
		width: 230px;
		display: flex;
		gap: var(--size-4);
		background: var(--background-fill-secondary);
		padding: 0 var(--size-4);
		cursor: default;
		padding-top: var(--size-2-5);
	}

	input[type="range"] {
		-webkit-appearance: none;
		appearance: none;
		width: 100%;
		height: 6px;
		border-radius: 3px;
		background: var(--neutral-400, #9ca3af);
		outline: none;
		margin: auto 0;
		border: none;
		padding: 0;
	}

	input[type="range"]::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 16px;
		height: 16px;
		border-radius: 50%;
		background: var(--color-accent, #f97316);
		cursor: pointer;
		border: none;
	}

	input[type="range"]::-moz-range-thumb {
		width: 16px;
		height: 16px;
		border-radius: 50%;
		background: var(--color-accent, #f97316);
		cursor: pointer;
		border: none;
	}
	span {
		width: 26px;
		color: var(--body-text-color);
	}
</style>
