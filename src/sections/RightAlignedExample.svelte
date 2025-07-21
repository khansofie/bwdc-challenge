<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>


<div>
    <Scroller layout="right">

        {#snippet scrolly()}
            <ArticleText>
                <strong>STEM degrees are a path to high-paying jobs and a financial stable life ahead. But the question is
                who's actually getting those jobs, and are they working in their field?</strong
                >
            </ArticleText>

            <ArticleText>
                The graph shows the current employment rates for STEM vs non-STEM jobs
            </ArticleText>

            <ArticleText>
                We have Nationwide American data on STEM vs. non-STEM Employment Rates 
                Among 25-34 years old with a STEM Degree
            </ArticleText>

            <ArticleText>
                It consists of male and female data, along with the following ethnicities: Black, Asian, Hispanic, and White
            </ArticleText>
        {/snippet}
    </Scroller>
</div>
