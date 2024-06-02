# Verdaccio with Deno (>1.44.0)

Small example how to install dependencies from a private registry using verdaccio an deno.

- Install dependencies (verdaccio itself) from a private registry
- Run verdaccio with `deno`

```bash
/// run verdaccio first in another tab
deno run --allow-env --allow-sys --allow-net --allow-read --allow-write main.ts
```

Deno requires some [permissions](https://docs.deno.com/runtime/manual/basics/permissions) to run verdaccio.

- `--allow-env`: Access to environment variables.
- `--allow-sys`: Access to the hostname
- `--allow-net`: Verdaccio it is a server
- `--allow-read`: For reading the local cache and configuration
- `--allow-write`: For the local cache and configuration

```typescript
import {runServer} from 'verdaccio';
(async () => {
    const app = await runServer(); // default configuration
    app.listen(4000, (event) => {
      // do something
    });
})();
```

```
// .npmrc
registry=http://localhost:4873
```

> Juan Picado, 2024.