<script>
    // `layout` can be either "right" or "left"
    // `sticky` and `scrolly` are the snippets passed in (see one of the examples)
    let { layout, sticky, scrolly } = $props(); 
    console.log("Scroller props:", { layout, sticky, scrolly });
</script>

<div class="wrapper {layout}">
    <div class="sticky">
        {@render sticky?.()}
    </div>

    <div class="scrolly">
        {@render scrolly?.()}
    </div>
</div>

<style>
    .wrapper {
        background-color: #220d31;
        border-style: solid;
        border-color: #220d31;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
        min-height: 100vh;
        position: relative;
    }

    .left .scrolly {
        order: 0;
    }

    .left .sticky {
        order: 1;
    }

    .right .scrolly {
        order: 1;
    }

    .right .sticky {
        order: 0;
    }

    .sticky,
    .scrolly {
        flex: 1 1 50%;
    }

    .sticky {
        position: sticky;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
        z-index: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #220d31;
        overflow: hidden;
        padding: 1.5rem;
        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .scrolly {
        z-index: 1;
        padding: 2rem 1.5rem;
        flex: 1 1 50%;
    }

    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: 2rem 1rem;
            width: 100vw;
        }

        .sticky {
            position: static;
            width: 100%;
            height: auto;
            background-color: #220d31;
            margin-bottom: 2rem;
        }

        .scrolly {
            z-index: 1;
            padding: 1rem;
        }
    }
</style>