<script>
    let { title, subtitle } = $props();
</script>

<div class="title-card">
    <div class="content">
        <h1>{title}</h1>
        <p>{@html subtitle}</p>
    </div>
</div>

<style>
    .title-card {
        background-color: #220d31;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 2rem;
        box-sizing: border-box;
        font-family: serif;
    }

    .content {
        max-width: 700px;
        background-color: #220d31;
        padding: 2rem;
        border: 6px solid #220d31;
        border-radius: 2rem;
        box-shadow: 16px 16px #220d31;
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #ffffff;
        text-shadow: 1px 1px 0 #220d31;
    }

    p {
        font-size: 1.3rem;
        color: #f7f5eb;
        margin-top: 1rem;
    }

    @media (max-width: 600px) {
        h1 {
            font-size: 2.2rem;
        }

        p {
            font-size: 1.1rem;
        }
    }
</style>
