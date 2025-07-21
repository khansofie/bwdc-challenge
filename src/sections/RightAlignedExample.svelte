<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>
<!--<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        chart: {
            
        },
        title: {
            
        },
        plotOptions: {
            pie: {
                allowPointSelect: true,
                dataLabels: [
                    {
                        enabled: true,
                        distance: 20,
                    },
                    {
                        enabled: true,
                        distance: -40,
                        format: "{point.percentage:.1f}%",
                        style: {
                            fontSize: "1.2em",
                            textOutline: "none",
                        },
                        filter: {
                            operator: ">",
                            property: "percentage",
                            value: 10,
                        },
                    },
                ],
            },
        },
        series: [
            {
                name: "Group",
                data: [
                    {
                        name: "Group 1",
                        y: 151,
                    },
                    {
                        name: "Group 2",
                        sliced: true,
                        selected: true,
                        y: 180,
                    },
                    {
                        name: "Group 3",
                        y: 32,
                    },
                    {
                        name: "Group 4",
                        y: 103,
                    },
                    {
                        name: "Group 5",
                        y: 77,
                    },
                ],
            },
        ],
    };
</script>-->

<div>
    <Scroller layout="right">
        <!--{#snippet sticky()}
            <div class="chart">
                <Chart {options} Highcharts={Highcharts} />
            </div>
        {/snippet}-->

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

<style>
   /* .chart {
        width: 90%;
        max-width: 600px;
        margin: 0 auto;
        display: block;
        text-align: center;
    }*/
</style>
