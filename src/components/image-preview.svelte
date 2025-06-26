<script lang="ts">
    interface ImagePreviewProps {
        imageSources: string[]
    }
    let { imageSources }: ImagePreviewProps = $props()
    let featuredImageIndex = $state(0)

    const changeFeaturedImage = (index: number) => {
        featuredImageIndex = index
    }
</script>
<div>

    <!-- TODO: better UI of no images -->
    {#if imageSources.length <= 0}
        <p>No images provided</p>
    {:else}

        <!-- featured image -->
        <img src={imageSources[featuredImageIndex]} alt="project thumbnail" class="featured-image"/>

        <div class="gallery">
            <!-- all images -->
            {#each imageSources as imageSource}
                <button type="button" onclick={() => changeFeaturedImage(imageSources.indexOf(imageSource))}>
                    <img src={imageSource} alt="project thumbnail"/>
                </button>
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

        &>button {
            max-width: 120px;
            transition: all 0.3s ease;
            border-radius: 0.5rem;
            border: none;
            cursor: pointer;
            &:hover {
                transform: scale(1.1);
            }
        }
    }
</style>