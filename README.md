[![Run unit tests](https://github.com/svelte-plugins/viewable/actions/workflows/run-unit.yml/badge.svg)](https://github.com/svelte-plugins/viewable/actions/workflows/run-unit.yml)
[![Run integration tests](https://github.com/svelte-plugins/viewable/actions/workflows/run-integration.yml/badge.svg)](https://github.com/svelte-plugins/viewable/actions/workflows/run-integration.yml)

# @svelte-plugins/viewable

A simple rule-based approach to tracking element viewability.

Try it in the [Svelte REPL](https://svelte.dev/repl/47fe04909fd14ee5ad5d02390cc147b1).

## Install

```bash
yarn add -D @svelte-plugins/viewable

# or with NPM

npm i -D @svelte-plugins/viewable
```

## Usage
```svelte
<script>
  import Viewable from "@svelte-plugins/viewable";

  const immediately = (definition) => {
    console.log('element has crossed the viewport');
  };

  const dwell = (definition) => {
    console.log(`${definition.percent}% of the element was visible for at least ${definition.duration} consecutive seconds`);
  };

  const rules = {
    // do something when the element enters the viewport
    immediately: { duration: 0, percentage: 0, fn: immediately },
    // do something when 50% of the element is visible for 4 seconds (consecutively)
    dwell: { duration: 4, percentage: 50, fn },
  };

  let element;
</script>

<Viewable {rules} {element}>
  <div bind:this={element}>Hello World</div>
</Viewable>
```

## Changelog

[Changelog](CHANGELOG.md)

## License

[MIT](LICENSE)
