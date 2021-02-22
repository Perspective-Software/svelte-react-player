<script>
    import { onMount } from 'svelte';
    import renderReactPlayer from './reactPlayer';

    // https://github.com/cookpete/react-player#props
    export let url = '';
    export let loop = false;
    export let light = false;
    export let volume = null;
    export let muted = false;
    export let playbackRate = 1;
    export let width = '640px';
    export let height = '360px';
    export let style = {};
    export let progressInterval = 1000;
    export let playsinline = false;
    export let pip = false;
    export let playing = false;
    export let controls = true;
    export let stopOnUnmount = true;
    export let fallback = null;
    export let wrapper = 'div';
    export let playIcon;
    export let previewTabIndex = 0;
    export let config = {};
    export let fluid = false;

    let playerElem;
    let mounted = false;

    // Reactivity
    let prevPlaying = playing;
    let prevUrl = url;
    let prevVolume = volume;

    onMount(() => {
        renderPlayer();
        mounted = true;
    });

    const renderPlayer = () => {
        const settings = {
            url,
            loop,
            light,
            volume,
            muted,
            playbackRate,
            width: fluid ? '100%' : width,
            height: fluid ? '100%' : height,
            style,
            progressInterval,
            playsinline,
            pip,
            fluid,
            playing,
            controls,
            stopOnUnmount,
            fallback,
            wrapper,
            playIcon,
            previewTabIndex,
            config,
            className: 'react-player',
        };

        renderReactPlayer(playerElem, settings);
    };

    $: if (mounted) {
        if (playing !== prevPlaying || url !== prevUrl || volume !== prevVolume) {
            renderPlayer();

            prevPlaying = playing;
            prevUrl = url;
            prevVolume = volume;
        }
    }
</script>

<div class:fluidWrapper={fluid}>
    <div bind:this={playerElem} />
</div>

<style>
    .fluidWrapper {
        position: relative;
        padding-top: 56.25%; /* Player ratio: 100 / (1280 / 720) = 16:9 */
    }

    .fluidWrapper :global(.react-player) {
        position: absolute;
        top: 0;
        left: 0;
    }
</style>
