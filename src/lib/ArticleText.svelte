<script>
    let { children } = $props();
</script>

<div class="article-text">
    <p>
        {@render children()}
    </p>
</div>

<style>
    .article-text {
        margin: 50vh auto;
        width: 50%;
        background-color: rgb(145, 43, 142);
        color: #ffffff;
        border: solid rgb(145, 43, 142) 3px;
        border-radius: 10px;
        padding: 20px;
    }
</style>
