<script>
  import Close from './close.svelte';
  export let showModal;
  export let insideClose = false;
  export let outsideClose = false;
  export let showHeader = true;
  export let showClose = true;
  let dialog;
  $: if (dialog && showModal) dialog.showModal();
  const inClose = (e) => {
    const target = e.target;
    if (insideClose && target?.tagName === 'BUTTON') dialog.close();
  };

  const outClose = (e) => {
    const target = e.target;
    if (outsideClose) dialog.close();
  };
</script>

<!-- svelte-ignore a11y-click-events-have-key-events a11y-no-noninteractive-element-interactions -->
<dialog
  bind:this={dialog}
  on:close={() => (showModal = false)}
  on:click|self={outClose}
>
  {#if showHeader}
    <div class="header">
      <slot name="header" />
      <!-- svelte-ignore a11y-autofocus -->

      {#if showClose}
        <button autofocus on:click={() => dialog.close()}>
          <Close />
        </button>
      {/if}
    </div>
  {/if}

  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div on:click={inClose}>
    <slot />
  </div>
</dialog>

<style>
  dialog {
    /* max-width: 32em; */
    border-radius: 0.8em;
    border: none;
    padding: 0;
  }
  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-top-right-radius: 0.8em;
    border-top-left-radius: 0.8em;
    height: 2.5em;
    background: gainsboro;
  }
  dialog::backdrop {
    background: rgba(0, 0, 0, 0.7);
  }
  dialog > div {
    padding: 1em;
  }
  dialog[open] {
    animation: zoom 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  @keyframes zoom {
    from {
      transform: scale(0.1);
    }
    to {
      transform: scale(1);
    }
  }
  dialog[open]::backdrop {
    animation: fade 0.2s ease-out;
  }
  @keyframes fade {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }
</style>
