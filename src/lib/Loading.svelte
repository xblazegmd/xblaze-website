<script lang="ts">
    import loadingCircle from "$lib/assets/loadingCircle.png";

    let { size } = $props();
</script>

<img src={loadingCircle} alt="Loading..." class="loading" style="width: {size}px"/>

<style>
    @keyframes spin {
        from {
            transform: rotate(0deg);
        }
        to {
            transform: rotate(360deg);
        }
    }

    .loading {
        mix-blend-mode: screen;
        animation: spin .9s linear infinite;
    }
</style>