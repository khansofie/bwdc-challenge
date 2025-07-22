<script>
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  let chart;

  const options = {
    chart: {
      type: "column",
      backgroundColor: "#ff99fc",
      borderColor: "#d0ddda",
      borderWidth: 5,
      borderRadius: 20,
      marginTop: 80,
    },
    title: {
      text: "High-Speed Broadband Usage in NYC Counties",
    },
    subtitle: {
      text: "Access to internet at 25 Mbps or higher",
    },
    xAxis: {
      categories: ["Bronx", "Kings", "Queens", "New York", "Richmond"],
      title: {
        text: "County",
      },
    },
    yAxis: {
      min: 0,
      max: 100,
      title: {
        text: "Percent of Households (%)",
      },
    },
    tooltip: {
      shared: true,
      valueSuffix: "%",
    },
    plotOptions: {
      column: {
        grouping: true,
        borderWidth: 0,
      },
    },
    series: [
      {
        name: "High-Speed Usage (25 Mbps+)",
        data: [50.0, 60.0, 70.0, 60.0, 70.0],
        color: "#4caf50",
      },
      {
        name: "Black Population %",
        data: [34.1, 29.0, 17.4, 14.0, 9.9],
        color: "#000080",
      },
    ],
  };
</script>

<div>
  <Scroller layout="center">
    {#snippet sticky()}
      <div class="sticky-container">
        <div class="chart">
          <Chart bind:chart {options} highcharts={Highcharts} />
        </div>

        <div class="explanation">
          <p>
            Broadband access isn't just about having internet—it's about speed. For video calls, remote work, streaming classes, and competitive job applications, households need connections of at least 25 Mbps.
          </p>
          <p>
            In boroughs with higher concentrations of Black residents, like the Bronx and Brooklyn, high-speed usage lags behind areas like Queens and Staten Island, where the Black population is smaller.
          </p>
          <p>
            This relationship between race and speed reveals deeper structural disparities: some communities have the infrastructure, pricing, and digital education to support fast, reliable internet. Others don’t.
          </p>
        </div>
      </div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        Not all internet access is equal. Slow speeds can make even basic digital participation—like uploading a résumé or attending class—nearly impossible.
      </ArticleText>

      <ArticleText>
        In the Bronx, where more than one-third of the population is Black, just 50% of households use internet at speeds of 25 Mbps or higher.
      </ArticleText>

      <ArticleText>
        In comparison, Queens and Staten Island show much higher high-speed usage, despite having significantly smaller Black populations.
      </ArticleText>

      <ArticleText>
        These patterns raise critical questions about equity: Is high-speed internet truly available—and affordable—for every neighborhood?
      </ArticleText>

      <ArticleText>
        As we layer this data with employment and education outcomes, we can see how digital access is foundational to opportunity.
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .chart {
    padding-top: 60px;
    width: 600px;
    max-width: 90vw;
    margin: 0 auto;
    padding-bottom: 40px;
  }

  .sticky-container {
    overflow: visible;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    min-height: 100vh;
    padding-top: 20px;
  }

  .explanation {
    max-width: 600px;
    margin: 20px auto;
    text-align: center;
    color: white;
  }
</style>