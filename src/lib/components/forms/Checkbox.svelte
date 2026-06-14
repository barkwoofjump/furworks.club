<script lang="ts">
  import type { Snippet } from "svelte";

  interface Props {
    id?: string;
    required?: boolean;
    checked?: boolean;
    children?: Snippet;
  }

  let { id = "", required = false, checked = $bindable(false), children }: Props = $props();
</script>

<label class="flex w-full items-start gap-2" for={id}>
  <input
    type="checkbox"
    {id}
    name={id}
    {required}
    bind:checked
    class="peer sr-only"
    aria-checked={checked} />
  <span
    class="flex size-5 items-center justify-center rounded border border-neutral-800 bg-neutral-900 transition-colors duration-75
  ease-out peer-checked:border-furworks peer-checked:bg-furworks peer-focus-visible:ring-2 peer-focus-visible:ring-furworks"
    aria-hidden="true">
    <span
      class={[
        "icon-[material-symbols--check-rounded] size-6 text-neutral-950 transition-opacity duration-75 ease-out",
        checked ? "opacity-100" : "opacity-0"
      ]}></span>
  </span>
  <span class="text-sm text-neutral-200">
    {@render children?.()}
  </span>
</label>
