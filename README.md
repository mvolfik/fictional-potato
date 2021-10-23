# Test repo for [sveltejs/language-tools#1214](https://github.com/sveltejs/language-tools/pull/1214)

```sh
cd /tmp/
git clone git@github.com:mvolfik/fictional-potato.git
cd fictional-potato
pnpm install
pnpm run check
# now you see output from current state

cd /tmp/
git clone git@github.com:mvolfik/language-tools.git
cd language-tools
git switch improve-sveltecomponent-bindthis
yarn install
yarn bootstrap
cd packages/svelte-check
yarn build
pnpm link --global

cd /tmp/fictional-potato # or wherever you cloned this
pnpm link --global svelte-check
pnpm run check
# now see the improved typecheck
```