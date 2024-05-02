
<script>
    import { ListBox, ListBoxItem } from '@skeletonlabs/skeleton';

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

<ListBox multiple>
    {#each Object.keys(servicios) as f}
        {#if group === 0 && f === 'centralita'}
        <span></span>
        {:else}
            <ListBoxItem bind:group={valueMultiple} name="medium" value={f}>{servicios[f].name}</ListBoxItem>
        {/if}
    {/each}
</ListBox>