# Vercel deployment

Set the Vercel project Root Directory to the repository root, not `app`. The root `vercel.json` exposes `app` at `/`, including page routes and static assets.

Only `app` is deployable. `app/packages/fnf` is a library-mode SDK; `app/packages/quanta` exports CSS and React components. They remain workspace dependencies, not HTTP services. No service bindings are needed: there are no calls between deployable services.

The service runs `bun run build:vercel`, selecting Nitro's Vercel preset and Node SSR resolution. The existing Cloudflare build remains available through `bun run build`. Unused Cloudflare binding examples are not part of the active website.

Run `vercel dev` from the repository root for local services testing. Run `cd app && bun run build:vercel` to verify production output without deploying.

Pending confirmation: name `app`, public catch-all routing, libraries excluded from services, and no bindings. Additional independent services require their entrypoints and intended public paths.
