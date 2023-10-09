<!-- svelte-ignore a11y-autofocus -->
<div class="close">
  <span />
  <span />
</div>

<style>
  .close {
    --width: 30px;
    cursor: pointer;
    background-color: red;
    width: var(--width);
    height: var(--width);
    border-radius: calc(var(--width) / 5);
    display: grid;
    place-items: center;
    position: relative;
  }

  .close span:nth-child(1),
  .close span:nth-child(2) {
    height: calc(var(--width) / 1.3);
    width: calc(var(--width) / 10);
    background-color: white;
    position: absolute;
  }

  .close span:nth-child(1) {
    transform: rotate(45deg);
  }

  .close span:nth-child(2) {
    transform: rotate(-45deg);
  }
  .close:hover {
    background: rgb(228, 95, 95);
  }
</style>
