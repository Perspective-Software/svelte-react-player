![NPM](https://img.shields.io/npm/l/svelte-react-player)

# svelte-react-player

Wrapper for the standalone version of [react-player](https://github.com/CookPete/react-player).

[Documentation & Demo](https://perspective-software.github.io/svelte-react-player/)

## Installation

`npm i svelte-react-player`

Enjoy:

```sveltehtml
<script>
    import { Player } from 'svelte-react-player'
</script>

<Player url="https://www.youtube.com/watch?v=NduTgkntfT4" />
```

## Props

| Prop   | Description  | Default |
| -------|:-------------| -------:|
| url    | Video URL    | ''
| fluid  | Toggle [fluid](https://github.com/CookPete/react-player#responsive-player) container| false
| config | Object of [react-player props](https://github.com/CookPete/react-player#props) | {}

## Development

`npm run dev` will start a local dev server on localhost:5000

Navigate to `http://localhost:5000/svelte-react-player` to see the docs.

Thanks to [@svelte-docs](https://github.com/AlexxNB/svelte-docs)!

