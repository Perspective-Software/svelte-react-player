## Fluid container

According to: https://github.com/CookPete/react-player#responsive-player

```example
<script>
    import { Player } from 'svelte-react-player';
</script>

<Player url="https://www.youtube.com/watch?v=NduTgkntfT4" fluid />
```

### Custom ratio

```example
<script>
    import { Player } from 'svelte-react-player';
</script>

<div style="width: 300px;">
    <Player url="https://www.youtube.com/watch?v=NduTgkntfT4" fluid ratio="300px" />
</div>
```
