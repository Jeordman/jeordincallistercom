<script lang="ts">
  import SideBar from "../components/sidebar/sidebar.svelte";
  // TODO: show loading spinner until mounted
</script>

<section id="content-wrapper">
  <SideBar />
  <section id="page">
    <slot />
  </section>
</section>

<style global lang="scss">
  * {
    padding: 0;
    margin: 0;
  }
  html,
  body {
    margin: 0;
    height: 100%;
  }

  #content-wrapper {
    display: flex;
    flex-direction: row;
    height: 100vh;
    width: 100vw;
  }

  #page {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
  }
</style>
