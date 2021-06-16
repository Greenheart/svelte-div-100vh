<script context="module">
    import { onMount } from 'svelte'
    import throttle from 'lodash-es/throttle'

    function isClient() {
        return typeof window !== 'undefined' && typeof document !== 'undefined'
    }

    function measureHeight() {
        if (!isClient()) return null
        return document.documentElement?.clientHeight || window.innerHeight
    }
</script>

<script>
    let height
    let container

    const updateHeight = throttle(() => {
        height = measureHeight()
        // Fallback to 100vh if used during server side rendering.
        container.style.height = `${height ? `${height}px` : '100vh'}`
    }, 16)

    onMount(() => {
        window.addEventListener('resize', updateHeight)
        updateHeight()
        return () => window.removeEventListener('resize', updateHeight)
    })
</script>

<div {...$$props} bind:this={container}>
    <slot />
</div>
