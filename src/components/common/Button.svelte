<script lang="ts">
  import type { Snippet } from "svelte";
  import type { HTMLButtonAttributes } from "svelte/elements";
  import { cn } from "../../utils/cn";
  interface ButtonProps {
    children?: Snippet;
    link?: string;
    type?: HTMLButtonAttributes["type"];
    xClass?: string;
  }

  const { children, link, type = "button", xClass, ...restProps }: ButtonProps = $props();

  const baseClass = cn(
    "font-bold text-sm block w-fit leading-none hover:opacity-70 transition-opacity py-[0.9375rem] px-8 text-white rounded-full [background:var(--gradient-green)]",
  );
</script>

{#if link !== undefined}
  <a href={link} {...restProps} class={cn(baseClass, xClass)}> {@render children?.()}</a>
{:else}
  <button {type} {...restProps} class={cn(baseClass, xClass)}> {@render children?.()}</button>
{/if}
