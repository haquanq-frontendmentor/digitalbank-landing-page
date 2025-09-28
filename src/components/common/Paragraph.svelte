<script lang="ts">
  import type { Snippet } from "svelte";
  import { cn } from "../../utils/cn";

  type ParagraphProps = {
    children?: Snippet;
    xClass?: string;
  };

  const { children, xClass }: ParagraphProps = $props();
</script>

<p class={cn("text-sm leading-4", xClass)}>{@render children?.()}</p>
