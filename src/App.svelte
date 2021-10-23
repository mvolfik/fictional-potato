<script lang="ts">
  import type { SvelteComponent } from "svelte";
  import { onMount } from "svelte";
  import Exact from "./Exact.svelte";
  import Simpler from "./Simpler.svelte";
  import Incorrect from "./Incorrect.svelte";

  type C = SvelteComponent & { action: (a: number) => number | string };
  let data: Record<string, C> = {};
  let e: C;
  let s: C;
  let i: C;

  let htmle: HTMLDivElement;
  let show = false;

  onMount(() => {
    let b: number | boolean = Math.random();
    if (b < 0.5) {
      b = false;
    }
    const a: number | string = b && "foo";
    console.log(a);
  });

  $: {
    console.log("Data:", data);
    console.log("Indi:", e, s, i);
    console.log("html:", htmle);
  }
</script>

{#each [{ k: "simpler", v: Simpler }, { k: "exact", v: Exact }, { k: "incorrect", v: Incorrect }, { k: "weird", v: true }] as { k, v } (k)}
  <svelte:component this={show ? v : null} bind:this={data[k]} />
{/each}

{#each [{ k: "simpler", v: Simpler }, { k: "exact", v: Exact }, { k: "incorrect", v: Incorrect }] as { k, v } (k)}
  <svelte:component this={show ? v : null} bind:this={data[k]} />
{/each}

{#each [{ k: "simpler", v: Simpler }, { k: "incorrect", v: Incorrect }] as { k, v } (k)}
  <svelte:component this={show ? v : null} bind:this={data[k]} />
{/each}

{#each [{ k: "simpler", v: Simpler }, { k: "exact", v: Exact }] as { k, v } (k)}
  <svelte:component this={show ? v : null} bind:this={data[k]} />
{/each}

{#if show}
  <Exact bind:this={e} />
  <Simpler bind:this={s} />
  <Incorrect bind:this={i} />

  <div bind:this={htmle} />
{/if}

<p><label><input type="checkbox" bind:checked={show} /> Show stuff</label></p>
