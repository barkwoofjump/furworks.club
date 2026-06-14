<script lang="ts">
  let { children } = $props();
</script>

<article class="container prose min-w-full font-manrope prose-invert">
  {@render children()}
</article>
