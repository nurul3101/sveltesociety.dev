<script>
  import { layout, page, metatags } from "@sveltech/routify";
  const nodes = $layout.parent.children.filter(r => !r.path.includes("/index"));
  export let title,
    description = "";

  $: metatags.title = title;
  $: metatags.description = description;

  $: metatags["twitter:title"] = title;
  $: metatags["twitter:description"] = description;
</script>

<h1>{title}</h1>

<slot />

<ul>
  {#each nodes as node}
    <li>
      <a href={node.path}>{node.meta.frontmatter.title}</a>
    </li>
  {/each}
</ul>
