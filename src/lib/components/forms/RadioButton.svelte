<script lang="ts">
  import type { Snippet } from "svelte";

  interface Props {
    name: string;
    group: string;
    value: string;
    required?: boolean;
    id?: string;
    children?: Snippet;
  }

  let {
    name,
    group = $bindable(),
    value,
    required = false,
    id = `radio-${value}`,
    children
  }: Props = $props();
</script>

<label class="flex w-full items-start gap-2" for={id}>
  <input
    type="radio"
    {name}
    bind:group
    {required}
    {value}
    {id}
    class="peer sr-only"
    aria-checked={group === value} />
  <span
    class="relative flex size-5 shrink-0 items-center justify-center rounded-full border border-neutral-800 bg-neutral-900 transition-colors duration-75
               ease-out peer-checked:border-furworks peer-checked:bg-furworks peer-focus-visible:ring-2 peer-focus-visible:ring-furworks
               before:absolute before:h-2 before:w-2 before:rounded-full before:bg-neutral-900 before:opacity-0
               before:transition-opacity before:duration-75 before:ease-out peer-checked:before:opacity-100"
    aria-hidden="true">
  </span>
  <span class="flex-1 text-sm leading-5 text-neutral-200">
    {@render children?.()}
  </span>
</label>
