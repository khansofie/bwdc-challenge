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
        background-color: #5c0e5a;
        color: #ffffff;
        border: solid #5c0e5a 3px;
        border-radius: 20px;
        padding: 20px;
        box-shadow: 16px 16px #5c0e5a;
    }
</style>
