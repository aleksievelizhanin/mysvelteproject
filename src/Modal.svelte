<script>
    export let showModal = false;
    export let isPromo = false;
    export let message;

</script>
{#if showModal}
<div class="backdrop" class:promo={isPromo == true} on:click|self>
    <div class="modal">
        <slot name="title"></slot>
        <slot></slot>
    </div>
</div>
{/if}

<style>
    .backdrop {
        width: 100%;
        height: 100%;
        position: fixed;
        background: rgba(0,0,0,0.8);
    }
    .modal {
        max-width: 400px;
        border-radius: 10px;
        padding: 10px;
        margin: 10% auto;
        text-align: center;
        background: white;
    }
    .promo .modal {
        background: crimson;
        color: white;
    }

</style>