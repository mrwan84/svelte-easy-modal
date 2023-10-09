# svelte-easy-modal

## Install

```bash
npm install --save svelte-easy-modal
```

## Usage

Import the `Modal` component into your main app component (e.g., `App.svelte`).

```svelte
<!-- App.svelte -->

<script>
  import Modal from 'svelte-easy-modal';
  let showModal = false;
  import Popup from './popup.svelte';
  $: console.log(showModal);
</script>

<main>
  <Modal
    showHeader={true}
    showClose={true}
    outsideClose={true}
    insideClose={true}
    bind:showModal
  >
    <h1 slot="header">Header</h1>
    <Popup />
  </Modal>
  <button on:click={() => (showModal = !showModal)}> OPEN MODAL </button>
</main>

<!-- popup.svelte -->

<main class="main">
  <h1>this is Popup</h1>
  <button>Close inside button</button>
</main>

<style>
  .main {
    width: 400px;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  button {
    width: 150px;
    height: 60px;
    font-size: 1.1rem;
    font-weight: bold;
  }
</style>

```
##Example
[svelte-easy-modal-example](https://github.com/mrwan84/svelte-easy-modal-example)
## API

### Component API

The `<Modal />` component accepts the following optional properties:

| Property         | Type    | Default | Description                              |
| ---------------- | ------- | ------- | ---------------------------------------- |
| **showModal**    | boolean | `null`  | to toggle the Modal.                     |
| **insideClose**  | boolean | `false` | to close the modal from a inside button. |
| **outsideClose** | boolean | `false` | self close modal.                        |
| **showHeader**   | boolean | `true`  | to show the header.                      |
| **showClose**    | boolean | `true`  | to show the close butten in the header.  |
