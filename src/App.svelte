<script lang="ts">
  import Counter from './lib/Counter.svelte'

  interface Counter {
    title: string
    count: number
  }

  const counterDefault: Counter = { title: 'new', count: 0 }
  let counters: Counter[] = [{ ...counterDefault }]

  $: countersTitleList = counters.map(({ title }) => title)
  $: sumOfCounters = counters.reduce((acc, { count }) => (acc += count), 0)

  function addCounter() {
    counters = [...counters, { ...counterDefault }]
  }
  function removeCounter(index: number) {
    counters = counters.toSpliced(index, 1)
  }
</script>

<main class="text-center">
  <h1 class="text-6xl leading-relaxed">Multiple Counter</h1>
  <div>
    <div class="max-w-sm mx-auto">
      <div>
        {#each counters as counter, idx}
          <div class="mb-2">
            <Counter
              bind:title={counter.title}
              bind:count={counter.count}
              on:delete={() => removeCounter(idx)}
            />
          </div>
        {/each}
      </div>
      <button
        type="button"
        class="w-full bg-green text-white rounded cursor-pointer"
        on:click={addCounter}>new counter</button
      >
    </div>
    <div>
      <p>title list: {countersTitleList.join(', ')}</p>
      <p>sum of count: {sumOfCounters}</p>
    </div>
  </div>
</main>
