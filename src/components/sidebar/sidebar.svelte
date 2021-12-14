<script lang="ts">
  import { onMount } from "svelte";
  import { fly } from "svelte/transition";
  import ToggleSideBarBtn from "./ToggleSideBarBtn.svelte";

  let showFullSideBar = false;
  let appWidth;
  $: forceShowSideBar = appWidth > 1100;

  onMount(() => {
    appWidth = window.innerWidth;
  });

  function toggleSideBar() {
    showFullSideBar = !showFullSideBar;
  }

  const animateSidebar = (node, args) =>
    args.clicked ? fly(node, args) : null;
</script>

<svelte:window bind:innerWidth={appWidth} />
<div id="sidebar-full">
  {#if showFullSideBar || forceShowSideBar}
    <nav
      in:animateSidebar={{
        clicked: showFullSideBar,
        x: -1000,
        opacity: 1,
        duration: 1000,
      }}
      out:animateSidebar={{
        clicked: showFullSideBar,
        x: -1000,
        opacity: 1,
        duration: 4000,
      }}
    >
      <div id="sidebar-main">
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/tech">Tech</a>
        <a href="/projects">projects</a>
      </div>
    </nav>
  {/if}
  <ToggleSideBarBtn {showFullSideBar} on:sidebar-click={toggleSideBar} />
</div>

<!-- 1100 media query -->
<style lang="scss">
  @media (min-width: 1100px) {
    #sidebar-full {
      position: relative !important;
    }
  }
  #sidebar-full {
    position: absolute;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  nav {
    height: 100%;
  }
  #sidebar-main {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    background-color: #f5f5f5;
    padding: 10px;
    min-width: 300px;
    height: 100%;
  }

  header {
    height: 65px;
    background-color: aquamarine;
  }

  nav a:hover {
    color: #f5f5f5;
    background-color: black;
  }

  #sidebar-main a {
    text-decoration: none;
    color: black;
  }
</style>
