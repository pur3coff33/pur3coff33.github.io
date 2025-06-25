<script lang="ts">
    import ImagePreview from "./image-preview.svelte";

    interface ProjectViewProps {
        imageSources: string[],
        title: string,
        subtitle: string,
        dateStarted: string,
        dateEnded: string,
        description: string,
        tags: string[],
        links: {
            github: string | null,
            demo: string | null
        }
    }

    let { imageSources, title, subtitle, dateStarted, dateEnded, description, tags, links }: ProjectViewProps = $props()
    
</script>
<div>
    <div class="container">
        <div class="info-container">
            <h2>{title}</h2>
            <span class="subtitle">{subtitle}</span>
            <span class="date">{dateStarted} - {dateEnded}</span>
            <p>{description}</p>
            <button class="btn read-more">Read More</button>
            <div class="tags">
                {#each tags as tag}
                    <span>{tag}</span>
                {/each}
            </div>
        </div>
        <ImagePreview imageSources={imageSources}/>

    </div>
    <div class="links">
        <a href={links.github} class="btn">VIEW SOURCE CODE</a>
        <a href={links.demo} class="btn primary">VIEW DEMO</a>
    </div>
</div>

<style>
    .container {
        display: flex;
        flex-direction: row;
        gap: 1rem;
    }
    .info-container {
        display: flex;
        flex-direction: column;
        flex: 2;
        gap: 1rem;

        &>h2 {
            text-transform: uppercase;
            letter-spacing: 0.15em;
            font-size: large;
            font-weight: 700;
        }
        .subtitle {
            font-weight: 500;
            font-size: medium;
        }
        .date {
            font-size: small;
            font-style: italic;
        }        
    }
    .read-more {
        max-width: 120px;
    }
    .links {
        display: flex;
        gap: 1rem;
    }
    .tags {
        margin: 1rem 0;
        display: flex;
        flex-wrap: wrap;
        gap: 0.3rem;
        &>span {
            padding: 0.3rem 2rem;
            background-color: var(--color-pale-light-25);
            color: var(--color-light);
            border-radius: 0.5rem;
            transition: all 0.3s ease;
            font-size: small;
        }
    }

    @media only screen and (max-width: 1200px) {
        .container {
            flex-direction: column-reverse;
        }
       
    }
</style>