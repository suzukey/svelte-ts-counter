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

<div
  class="flex items-center justify-between bg-light rounded shadow-lg px-4 py-2"
>
  <input type="text" class="w-1/3 text-gray-600" bind:value={title} />
  <span class="text-lg font-bold">{count}</span>
  <div class="flex items-center">
    <div class="flex items-center rounded-xl text-white">
      <button
        type="button"
        class="bg-red rounded-l px-3 py-1"
        on:click={increment}>+</button
      >
      <button type="button" class="bg-blue px-3 py-1" on:click={decrement}
        >-</button
      >
      <button
        type="button"
        class="bg-yellow rounded-r border-r px-3 py-1"
        on:click={reset}>0</button
      >
    </div>
    <button
      type="button"
      class="ml-4 text-gray"
      on:click={() => dispatch('delete')}>x</button
    >
  </div>
</div>
