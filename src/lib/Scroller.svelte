<script>
    // `layout` can be either "right" or "left"
    // `sticky` and `scrolly` are the snippets passed in (see one of the examples)
    let { layout, sticky, scrolly } = $props(); 
</script>

<div class="wrapper {layout}">
    <div class="sticky">
        {@render sticky()}
    </div>

    <div class="scrolly">
        {@render scrolly()}
    </div>
</div>

<style>
    .wrapper {
        background-color: #220d31;
        /*padding: min(100vh, 30rem) 1rem;*/
        border-style: solid;
        border-color: #220d31;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
        min-height: 100vh;
        position: relative;
    }
    /*Layout order*/
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
        /*display: flex;*/
        /*flex-direction: column;*/
        flex: 1 1 50%; /* Allows growing, shrinking */
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
        box-shadow: 0 4px 12 px rgba(0,0,0,0.1);
    }

    .scrolly {
        z-index: 1;
        /*padding-left: 1.5rem;
        padding-right: 1.5rem;*/
        padding: 2rem 1.5rem;
        /*justify-content: flex-start;*/
        flex: 1 1 50%;
    }

    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: 2rem 1rem;
            width: 100vw;
        }

        /*.sticky,*/
        /*.scrolly {*/
            /*flex: 1 1 auto;*/
            /*min-width: 100%;*/
            /*position: static; remove sticky on mobile */
            /*transform: none;/*
        /*}*/

        /*.sticky {*/
            /*margin-bottom: 2rem;*/
            /*min-height: auto;*/
            /*background-color: #ffb6c1;*/
        /*}*/

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
