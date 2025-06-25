<script lang="ts">

    import GithubIcon from "../assets/icons/github-icon.svelte"
    import LinkedinIcon from "../assets/icons/linked-icon.svelte"

    interface ContactProps {
        email: string,
        github: string,
        linkedin: string
    }

    let { email, github, linkedin }: ContactProps = $props()
</script>

<div class="container">

  
    <div class="content">
        <h2>Thanks for checking out my portfolio</h2>
        <p>You can reach me out at <a href={`mailto:${email}`}>{email}</a></p>

        <div class="socials">
            <a href={github} aria-label="github">
                <GithubIcon />
            </a>
            <a href={linkedin} aria-label="linkedin">
                <LinkedinIcon />
            </a>
        </div>

        <span class="year">{new Date().getFullYear()}</span>
    </div>  


    <!-- LINES -->
    <div class="line top left"></div>
    <div class="line top right"></div>
    <div class="line bottom left"></div>
    <div class="line bottom right"></div>
</div>


<style>

    :global(:root) {
        --line-width: 1px;
        --line-overlap: 3rem;
    }


    .container {
        background-color: var(--color-dark);
        padding: calc(var(--line-overlap) + 1rem); 
        border-radius: 1rem;
        position: relative;

    }

    .content {
        position: relative;
        overflow: hidden;
        
        &>.year {
            position: absolute;
            top: 0;
            right: 0;
            color: var(--color-pale-light-25);
            font-size: 50px;
            font-weight: 700;
            writing-mode: sideways-rl;
        }
    }
        

    /* email */
    a[href^="mailto:"] {
        color: var(--color-light);
        font-weight: 700;
        text-decoration-line: underline;
        text-decoration-color: var(--color-pale-light);
        transition: all 0.3s ease;
        &:hover {
            color: var(--color-pale-light);
        }
    }

    .socials {
        display: flex;
        gap: 1rem;
        margin: 1rem 0;

        &>a {
            color: var(--color-light);
        }
    }

   

    .line {
        position: absolute;
        width: 100%;
        height: var(--line-width);
        background-color: var(--color-pale-light-25);
    }

    .top {
        top: 0;
    }

    .bottom {
        bottom: 0;
    }

    .left {
        left: 0;
    }

    .right {
        right: 0;
    }

    /* make verticals lines */
    .top.right, .bottom.left {
        width: var(--line-width);
        height: 100%;
    }

    /* make lines overlap */
    .top.left {
        top: var(--line-overlap);
    }
    .bottom.right {
        bottom: var(--line-overlap);
    }

    .top.right {
        right: var(--line-overlap);
    }
    .bottom.left {
        left: var(--line-overlap);
    }

    

</style>