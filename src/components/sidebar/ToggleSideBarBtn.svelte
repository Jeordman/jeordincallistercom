<script lang="ts">
  import { fly, crossfade } from "svelte/transition";
  import { createEventDispatcher } from "svelte";
  import Icon from "svelte-awesome";
  import { bars } from "svelte-awesome/icons";
  let dispatch = createEventDispatcher();

  export let showFullSideBar;

  function handleSideBarClick(e: MouseEvent) {
    console.log("clicke");
    dispatch("sidebar-click", e);
  }
</script>

<button on:click={handleSideBarClick}>
  <Icon data={bars} />
</button>

<style lang="scss">
  @media (min-width: 1100px) {
    button {
      display: none !important;
    }
  }
  button {
    position: absolute;
    background: #eee;
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    font-size: 16px;
    height: fit-content;
    width: fit-content;
    border-radius: 8px;
    background-color: rgba(255, 255, 255, 0.356);
    display: flex;
  }
  button:hover {
    cursor: pointer;
  }
</style>
