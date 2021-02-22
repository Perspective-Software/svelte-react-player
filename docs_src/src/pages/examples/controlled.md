## Controlled

```example
<script>
    import { Player } from 'svelte-react-player';
    
    let playing = false;
    let url = 'https://vimeo.com/217499569';
    let volume = null;
    
    const handlePlay = () => playing = true;
    const handlePause = () => playing = false;
</script>

<button on:click={handlePlay}>Play</button>
<button on:click={handlePause}>Pause</button>
<select bind:value={url}>
    <option value="https://www.youtube.com/watch?v=NduTgkntfT4">YouTube</option>;
    <option value="https://vimeo.com/217499569">Vimeo</option>
    <option value="https://home.wistia.com/medias/e4a27b971d">Wistia</option>
    <option value="https://www.dailymotion.com/video/x5e9eog">Dailymotion</option>
    <option value="https://www.twitch.tv/videos/106400740">Twitch</option>
    <option value="https://streamable.com/moo">Streamable</option>
    <option value="https://www.facebook.com/facebook/videos/10153231379946729/">Facebook</option>
    <option value="https://video.vidyard.com/watch/YBvcF2BEfvKdowmfrRwk57">Vidyard</option>
    <option value="https://soundcloud.com/miami-nights-1984/accelerated">Soundcloud</option>
    <option value="https://www.mixcloud.com/mixcloud/meet-the-curators/">Mixcloud</option>
</select>
<input type="range" bind:value={volume} min="0" max="1" step="0.1" />

<Player {url} {playing} {volume} {controls}/>
```
