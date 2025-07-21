<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
        {
            name: "Asian",
            data: [
                [2016, 8.4],
                [2023, 6.9],
            ],
            color: "#8427c9",
        },
        {
            name: "Black",
            data: [
                [2016, 7.7],
                [2023, 6.1],
            ],
            color: "#ff99fc",
        },
        {
            name: "Hispanic",
            data: [
                [2016, 6.5],
                [2023, 5.9],
            ],
            color: "#4096fa",
        },
        {
            name: "White",
            data: [
                [2016, 5.7],
                [2023, 4.8],
            ],
            color: "#4099fa",
        },
    ];

    let chart;
    let thirdSeriesVisible = false;

    let options = {
        chart: {
            type: "spline",
            backgroundColor: "#e3ff00",
            borderColor: "#007052",
            borderWidth: 5,
            borderRadius: 20,
        },
        title: {
            text: "STEM vs. non-STEM Employment Rates Among 25-34 Year Olds with a STEM Degree",
        },
        subtitle: {
            text: "Nationwide",
        },
        series: [series[0], series[1]],
    };

    function toggleThirdSeries() {
        const seriesName = "Hispanic";
        const existingSeries = chart.series.find((s) => s.name === seriesName);

        if (existingSeries) {
            existingSeries.remove();
            thirdSeriesVisible = false;
        } else {
            chart.addSeries(series.find(s => s.name === seriesName));
            thirdSeriesVisible = true;
        }
    }
</script>

<div>
    <Scroller layout="center">
        {#snippet sticky()}
        <div class="sticky-container">
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
            <button on:click={toggleThirdSeries} class="toggle-button">
                {thirdSeriesVisible ? "Remove Group 3" : "Add Group 3"}
            </button>
            <div class="explanation">
            <div>
                <p>
                    You can use Svelte to add and remove data from a Highcharts
                    chart.
                </p>
                <p>
                    When you click the button above, a third group is toggled in
                    the chart. Check out the source code to see how it's done.
                </p>
                <p>
                    <strong
                        >🤔 How might you use other HTML elements, like
                        checkboxes or radio buttons, in a similar way to filter
                        data?</strong
                    >
                </p>
            </div>
            </div>
        </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                STEM degrees are a path to high-paying jobs and a financial stable life ahead. But the question is
                who's actually getting those jobs, and are they working in their field?
            </ArticleText>

            <ArticleText>
                The graph shows the current employment rates for STEM vs non-STEM jobs
            </ArticleText>

            <ArticleText>
                You might also want to add more interactivity or gamify parts of
                your scrollytelling piece.
            </ArticleText>

            <ArticleText>
                <strong>
                    It's up to you to research how to create the effects and
                    functionality that you envision!
                </strong>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 600px;
        max-width: 90vw;
        margin: 0 auto;
    }

    .toggle-button {
        margin: 20px auto;
        padding: 15px 30px;
        color: #007052;
        background-color: #0bd956;
        border: solid 2px #007052;
        border-radius: 16px;
        font-size: large;
        cursor: pointer;
        transition: all 0.2s ease;
        box-shadow: 0 4px 0 #007052;
    }

    .toggle-button:active {
        transform: translateY(2px);
        box-shadow: 0 2px 0 #007052;
    }

    .sticky-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .explanation {
        max-width: 600px;
        margin: 20px auto;
        text-align: center;
    }
</style>
