<script>
    import { onMount } from 'svelte';
    import player from './reactPlayer';

    export let url = '';
    export let config = {
        controls: true,
        playing: false,
    }; // https://github.com/cookpete/react-player#props
    export let fluid = false;

    let playerElem;

    onMount(() => {
        player(playerElem, {
            url,
            className: fluid ? 'react-player' : undefined,
            ...config,
            width: fluid ? '100%' : config.width,
            height: fluid ? '100%' : config.height,
        });
    });
</script>

<div class:fluidWrapper={fluid}>
    <div bind:this={playerElem} />
</div>

<style>
    .fluidWrapper {
        position: relative;
        padding-top: 56.25%; /* Player ratio: 100 / (1280 / 720) = 16:9 */
    }

    :global(.react-player) {
        position: absolute;
        top: 0;
        left: 0;
    }
</style>
