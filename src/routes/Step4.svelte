<script>

    /**
     * @type {number}
     */
     export let group;

    /**
     * @type {string[]}
     */
     export let valueMultiple;

    /**
     * @type {string}
     */
     export let cliente;

     /**
     * @type {{ [x: string]: { name: any; }; }}
     */
     export let servicios;
</script>

<h2>Cliente: {cliente}</h2>

{#each valueMultiple as servicio }
{#if group === 0 && servicio === 'centralita'}
<span></span>
{:else}
    <div class="flex justify-center space-x-2">
        <h2>{servicios[servicio].name}:</h2>
        <span>{servicios[servicio].values[servicios[servicio].selectedValue-1].label}</span>
    </div>
{/if}
{/each}