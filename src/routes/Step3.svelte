
<script>
	import { RadioGroup, RadioItem } from '@skeletonlabs/skeleton';

    /**
     * @type {number}
     */
    export let group;

    /**
     * @type {string[]}
     */
     export let valueMultiple;

     /**
     * @type {{ [x: string]: { name: any; }; }}
     */
     export let servicios;
</script>

{#each valueMultiple as f}
{#if group === 0 && f === 'centralita'}
<span></span>
{:else}
<div class="justify-center space-x-2">
    <h2>{servicios[f].name}</h2>
    <RadioGroup>
    {#each servicios[f].values as v}
        <RadioItem bind:group={servicios[f].selectedValue} name={f} value={v.value}>{v.label}</RadioItem>
    {/each}
    </RadioGroup>
</div>
{/if}
{/each}