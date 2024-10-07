<script>
    import { onMount } from 'svelte';
    import loadjs from 'loadjs';

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
    export let ratio = '56.25%'; /* Player ratio: 100 / (1280 / 720) = 16:9 */

    export let callbacks = {};

    let playerElem;
    let mounted = false;

    // Reactivity
    let prevPlaying = playing;
    let prevUrl = url;
    let prevVolume = volume;


    onMount(() => {
        mounted = true;

        loadjs('https://cdn.jsdelivr.net/npm/react-player@2.16.0/dist/ReactPlayer.standalone.min.js', {
            success() {
                renderPlayer();
            },
            error() {
                console.error('Failed to load the ReactPlayer script');
            },
        });
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
            ...callbacks,
        };

        if (typeof window.renderReactPlayer === 'function') window.renderReactPlayer(playerElem, settings);
        else console.error('Unable to find react player on window object');
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

<div class:fluidWrapper={fluid} style="{fluid ? `padding-top: ${ratio}` : ''}">
    <div bind:this={playerElem} />
</div>

<style>
    .fluidWrapper {
        position: relative;
        width: 100%;
    }

    .fluidWrapper :global(.react-player) {
        position: absolute;
        top: 0;
        left: 0;
    }
</style>
