<script>
    import Div100vh from './Div100vh.svelte'
</script>

<Div100vh style="background: red;">
    <div class="fullscreen-demo">
        This blue area should be fullscreen on all devices.
    </div>
</Div100vh>

<style>
    :global(html, body) {
        height: 100%;
        overscroll-behavior-y: contain;
        margin: 0;
    }
    :global(*) {
        -webkit-tap-highlight-color: transparent;
        box-sizing: border-box;
    }
    :global(button::-moz-focus-inner) {
        border: 0;
    }
    :global(:focus, *:focus) {
        outline: 0 !important;
        border: 0 !important;
    }

    .fullscreen-demo {
        height: 100%;
        background: lightskyblue;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 2rem;
        font-weight: 600;
        padding: 32px;
    }
</style>
