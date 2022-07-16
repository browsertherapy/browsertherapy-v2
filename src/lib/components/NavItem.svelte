<script>
  import { currentPage, isMenuOpen } from '$lib/assets/js/store'

  export let href
  export let page

  page = page.replace(' ', '-'); // for use as classes

  $: isCurrentPage = $currentPage.startsWith(href)

  const maybeCloseMenu = () => {
    if (href != $currentPage) {
      isMenuOpen.set(false)
    }
  }
</script>


<li>
  <a
    href={href}
    on:click={maybeCloseMenu}
    class={page}
    class:active={isCurrentPage}
    aria-current={isCurrentPage ? 'page' : false}
  >
    <slot />
  </a>
</li>