<script>
  import Header from '~/layout/Header.svelte'
  import Title from '~/layout/NewTitle.svelte'
  import SocialLinks from '~/layout/SocialLinks.svelte'
  import Transition from '~/layout/Transition.svelte'
  import { page } from '$app/stores'
  import '../app.scss'

  $: key = $page.url.pathname
  $: console.log({ key })
</script>

<svelte:head>
  <link rel="icon" type="image/svg" href="/favicon.png" />
  <title>Kevin R. Whitley</title>
  <meta name="description" content="The personal bio of open source author Kevin R. Whitley." />
  <meta name="robots" content="index, follow, max-snippet:-1, max-image-preview:large, max-video-preview:-1" />
  <html lang="en" />
</svelte:head>

<style lang="scss">
  main {
    --padding: 5em;
    display: flex;
    flex-flow: column;
    align-items: stretch;
    margin: 0 1em;
    position: relative;
    padding: 0 var(--padding);
    opacity: 1;
    text-align: center;

    @media (max-width: 50em) {
      --padding: 7vw;
    }

    section {
      padding: 2em 0 3em;
      height: auto;
      overflow: hidden;
      display: block;
      text-align: left;
      border-bottom: 1px solid var(--foreground-color);

      &:empty {
        outline: none;
        height: 0;
        border-bottom: none;
      }
    }
  }
</style>

<main>
  <Title />

  <Transition refresh={key}>
    <section>
      <slot />
    </section>
  </Transition>

  <SocialLinks />
</main>
