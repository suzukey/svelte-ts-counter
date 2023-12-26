<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher<{ delete: void }>()

  export let title: string
  export let count: number

  function increment() {
    count++
  }
  function decrement() {
    if (count > 0) count--
  }
  function reset() {
    count = 0
  }
</script>

<div class="flex">
  <input type="text" bind:value={title} />
  <span>{count}</span>
  <div>
    <button type="button" on:click={increment}>+</button>
    <button type="button" on:click={decrement}>-</button>
    <button type="button" on:click={reset}>0</button>
  </div>
  <button type="button" on:click={() => dispatch('delete')}>x</button>
</div>
