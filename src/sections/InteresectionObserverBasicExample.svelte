<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        chart: {
            type: "pie",
        },
        title: {
            text: "Degree Attainment by Race or Ethnicity ",
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
                name: "Race/Ethnicity",
                data: [
                    { name: "Asian", y: 404 },
                    { name: "Black", y: 186, sliced: true, selected: true },
                    { name: "White", y: 272 },
                    { name: "Hispanic", y: 138 },
                ],
            },
        ],
    };
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <div class="chart">
                <Chart {options} Highcharts={Highcharts} />
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                Education is one of the most powerful tools for social and economic mobility. 
                But not all groups have equal access to higher education.
                This graph shows how degree attainment varies across different racial and ethnic groups.
            </ArticleText>

            <ArticleText>
                Understanding these gaps is crucial for policymakers, educators, and members of the community
                who are aiming to close the education gaps and create equal opportunities for all.
            </ArticleText>

            <ArticleText>
                Why do some racial and ethnic groups attain degrees at higher rates than others?
                What factors might be driving these differences?
            </ArticleText>

            <ArticleText>
                Behind these numbers are millions of students striving to earn degrees and build futures.
                Yet their chances are not always the same.
            </ArticleText>

            <ArticleText>
                As we explore this data, we've seen how degree attainment influences employment outcomes,
                and how even internet access plays a surprising role in shaping those opportunities.
            </ArticleText>

            <ArticleText>
                Across all four graphs, one pattern stands out: racial disparities in education and employment
                are deeply intertwined with access to technology and infrastructure.
            </ArticleText>

            <ArticleText>
                When communities lack fast, reliable internet, they face barriers to online learning, job searching,
                telehealth, and more—limiting social mobility in the digital age.
            </ArticleText>

            <ArticleText>
                <strong>What's next?</strong> We can act. Investing in broadband infrastructure, expanding equitable STEM
                opportunities, and addressing systemic disparities are crucial steps.
            </ArticleText>

            <ArticleText>
                Change begins with awareness—but it grows with action.
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        max-width: 600px;
        margin: 0 auto;
        display: block;
        text-align: center;
    }

    .article-text {
        color: white;
    }
</style>