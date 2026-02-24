<!--
@component
This is the LAYOUT file.
It wraps every page on your site.
Use it for headers, footers, and navigation that appear on all pages.
-->
<script>
  // Import global styles
  import '../app.scss';
  
  // Import site-wide components
  import SiteHeader from '$lib/components/SiteHeader.svelte';
  import SiteFooter from '$lib/components/SiteFooter.svelte';
  import { page } from '$app/stores';
  import { derived } from 'svelte/store';

  // In Svelte 5, we use $props() to receive the page content
  let { children } = $props();

  // Hide site chrome (header/footer) when on the root page so individual
  // pages like the Tip Calculator can render alone.
  const showChrome = derived(page, ($page) => $page.url.pathname !== '/');

  // Navigation links for the header (matching real NYCity News Service)
  const navLinks = [
    { label: 'Arts & Culture', href: 'https://www.nycitynewsservice.com/nycns_topics/arts-culture/' },
    { label: 'Business', href: 'https://www.nycitynewsservice.com/nycns_topics/business/' },
    { label: 'Education', href: 'https://www.nycitynewsservice.com/nycns_topics/education/' },
    { label: 'Environment', href: 'https://www.nycitynewsservice.com/nycns_topics/environment/' },
    { label: 'Health', href: 'https://www.nycitynewsservice.com/nycns_topics/health/' },
    { label: 'Housing', href: 'https://www.nycitynewsservice.com/nycns_topics/housing/' },
    { label: 'Politics', href: 'https://www.nycitynewsservice.com/nycns_topics/politics/' },
    { label: 'El Deadline', href: 'https://eldeadline.nycitynewsservice.com/' },
    { label: 'The Bronx', href: 'https://motthavenherald.com/' },
  ];
</script>

{#if $showChrome}
  <SiteHeader {navLinks} />
{/if}

<main>
  <!-- This renders the current page's content -->
  {@render children()}
</main>

{#if $showChrome}
  <SiteFooter />
{/if}

<style>
  /* Styles here only apply to this layout */
  main {
    min-height: calc(100vh - 200px); /* Ensure footer stays at bottom */
  }
</style>