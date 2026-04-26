<script lang="ts">
    import sliderGroove from "$lib/assets/slidergroove.png";
    let { progress, max } = $props();

    let percent = $derived((progress / max) * 100);
</script>

<div class="progress">
    <img src={sliderGroove} alt="border" class="border">
    <div class="fill" style="width: {percent}%;"></div>
</div>

<style>
    .progress {
        position: relative;
        width: 550px;
        height: 27px;
        border-radius: 100px;
        overflow: hidden;
    }

    .fill {
        height: 100%;
        background-image: url("$lib/assets/sliderBar.png");
        background-repeat: repeat-x;
        background-size: auto 100%;
    }

    .border {
        position: absolute;
        top: 50%;
        left: 0;
        transform: translateY(-50%);
        width: 100%;
        z-index: 100;
    }

    @media (max-width: 548px) {
        .progress {
            width: 400px;
        }

        .fill {
            height: 100%;
            transform: translate(6px, 4px); /* If it works it works */
            background-size: auto 60%;
        }
    }
</style>