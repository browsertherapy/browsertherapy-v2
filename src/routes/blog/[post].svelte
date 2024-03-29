<!-- This file renders each individual blog post for reading. Be sure to update the svelte:head below -->

<script context="module">
  export const load = async ({ params }) => {
    try {  
      const allPosts = await import.meta.glob(`../../lib/posts/*.md`)
      const iterablePosts = Object.entries(allPosts)

      let filteredPosts = iterablePosts.filter(([path, resolver]) => {
        return path.slice(27, -3) === params.post
      })
      if (Array.isArray(filteredPosts) && filteredPosts.length === 1) {
        // Chop off `../../lib/posts/` and `.md` so Vite doesn't complain about dynamic imports
        // https://github.com/rollup/plugins/tree/master/packages/dynamic-import-vars#limitations
        const postFileName = filteredPosts[0][0].slice(16,-3);
        const post = await import(`../../lib/posts/${postFileName}.md`)

        return {
          props: {
            PostContent: post.default,
            meta: { ...post.metadata, slug: params.post } 
          }
        }
      }
      return {
        props: {}
      }
    } catch(error) {
      return {
        status: 404,
        error: error.message
      }
    }
  }
</script>


<script>
  export let PostContent
  export let meta

  const { title, excerpt, date, updated, coverImage, coverWidth, coverHeight, categories } = meta
</script>


<svelte:head>
  <!-- Be sure to add your image files and un-comment the lines below -->
  <title>{title}</title>
  <meta data-key="description" name="description" content="{excerpt}">
  <meta property="og:type" content="article" />
  <meta property="og:title" content={title} />
  <meta name="twitter:title" content={title} />
  <meta property="og:description" content={excerpt} />
  <meta name="twitter:description" content={excerpt} />
  <!-- <meta property="og:image" content="https://yourdomain.com/image_path" /> -->
  <meta property="og:image:width" content={coverWidth} />
  <meta property="og:image:height" content={coverHeight} />
  <!-- <meta name="twitter:image" content="https://yourdomain.com/image_path" /> -->
</svelte:head>


<article class="post">
  <!-- You might want to add an alt frontmatter attribute. If not, leaving alt blank here works, too. -->
  <img
    class="cover-image"
    src="{coverImage}"
    alt=""
    style="aspect-ratio: {coverWidth} / {coverHeight};"
    width={coverWidth}
    height={coverHeight}
  />

  <h1>{ title }</h1>
  
  <div class="meta">
    <b>Published:</b> {date}
    <br>
    <b>Updated:</b> {updated}
  </div>
  
  <svelte:component this={PostContent} />

  {#if categories}
    <aside class="post-footer">
      <h2>Posted in: </h2>
      <ul>
        {#each categories as category}
          <li>
            <a href="/blog/category/{category}/">
              { category }
            </a>
          </li>
        {/each}
      </ul>
    </aside>
  {/if}
</article>