<script lang="ts">
    interface ImagePreviewProps {
        imageSources: string[]
    }
    let { imageSources }: ImagePreviewProps = $props()
</script>
<div>

    <!-- TODO: better UI of no images -->
    {#if imageSources.length <= 0}
        <p>No images provided</p>
    {:else}

        <!-- featured image -->
        <img src={imageSources[0]} alt="project thumbnail" class="featured-image"/>

        <div class="gallery">
            <!-- all images -->
            {#each imageSources as imageSource}
                <img src={imageSource} alt="project thumbnail"/>
            {/each}
        </div>
    {/if}

</div>  

<style>
    div {
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }
    img {
        width: 100%;
        height: auto;
        object-fit: cover;
        aspect-ratio: 16/9;
        border-radius: 0.5rem;
    }
    .featured-image {
        max-width: 400px;
    }
    .gallery {
        display: flex;
        flex-direction: row;
        gap: 1rem;

        &>img {
            max-width: 120px;
        }
    }
</style>