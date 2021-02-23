## Callbacks

See https://github.com/cookpete/react-player#callback-props for a list of possible callbacks.

```example
<script>
    import { Player } from 'svelte-react-player';
    
    let url = 'https://vimeo.com/217499569';
    
    const handleProgress = (progress) => console.log(progress);
    const handlePlay = () => console.log('play!');
    const handlePause = () => console.log('paused');
    
    const callbacks = {
        onProgress: handleProgress,
        onPlay: handlePlay,
        onPause: handlePause,
    };
</script>

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

<p>Now playing: {url}</p>

<Player {url} {callbacks} />
```
