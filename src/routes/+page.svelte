<script lang="ts">
    import lightsaberoff from "$lib/lightsaber_off.png"
    import lightsaberon from "$lib/lightsaber_on.png"

    let ison = false;
    let height = 450;
    let angle = 0;

    const onClick = () => {
        ison = !ison;
    };
    const onMove = (e:MouseEvent) => {
        let bh = document.body.clientHeight / 2;
        let bw = document.body.clientWidth / 2;
        let divh = e.clientY - bh;
        let divw = e.clientX - bw;
        angle = (Math.atan2(divw, divh) / Math.PI * 180 - 90) * -1;
    };
</script>

<div class="container" on:click={onClick} on:mousemove={onMove}>
    {#if ison}
        <img src={lightsaberon} alt="Manfred" style="--height:{height}; transform: rotate({angle}deg)">
    {:else}
        <img src={lightsaberoff} alt="Manfred" style="--height:{height}; transform: rotate({angle}deg)">
    {/if}
</div>

<style>
    .container{
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        width: 100vw;
    }
    img{
        height: calc(var(--height) * 1px);
        width: calc(var(--height) * 163/54 * 1px); 
        user-select: none;
        pointer-events: none;
    }
</style>