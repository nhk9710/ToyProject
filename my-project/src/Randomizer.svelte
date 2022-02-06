<script>
    export let list;
    let chosen = '두근두근';
    let luckCount= 0;

    const choose = (e) => {
        e.preventDefault();
        chosen = list[Math.floor(Math.random() * list.length)].item.toUpperCase();
        luckCount++;
    }
</script>
<div class="randomize-box">
    <p class="chosen">{chosen}</p>

    {#if luckCount === 0}
    <button class="btn" on:click={choose}>당신의 운세는??</button>
        {:else if luckCount!==0}
        <button class="btn" disabled>하루에 한번만 보세요^^</button>
    {/if}
        </div>
<style>
    .chosen{
        margin-bottom: 20px;
        font-size: 5em;
        font-weight: bolder;
    }
</style>