## Controlled

```example
<script>
    import { Player } from 'svelte-react-player';
    
    let playing = false;
    
    const handlePlay = () => playing = true;
    const handlePause = () => playing = false;
</script>

<button on:click={handlePlay}>Play</button>
<button on:click={handlePause}>Pause</button>

<Player url="https://vimeo.com/217499569" {playing} />
```
