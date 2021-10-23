# Test repo for [sveltejs/language-tools#1214](https://github.com/sveltejs/language-tools/pull/1214)

```sh
cd /tmp/

# <needed until='https://github.com/Rich-Harris/magic-string/pull/193 is merged'>
git clone git@github.com:mvolfik/magic-string.git
cd magic-string
git switch feature-copy
npm install
npm run build
yarn link
cd ..
# </needed>

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
# <needed ref='-1'> <!-- you know what I mean -->
yarn link magic-string
# </needed>
yarn bootstrap
cd packages/svelte-check
yarn build
pnpm link --global

cd /tmp/fictional-potato # or wherever you cloned this
pnpm link --global svelte-check
pnpm run check
# now see the improved typecheck
```