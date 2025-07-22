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
      text: "Broadband Internet Subscription by Race in NYC Urban Counties",
    },
    subtitle: {
      text: "Black Households vs. All Households",
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
        text: "Percent of Households with Broadband (%)",
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
        name: "All Households",
        data: [88.4, 88.5, 93.0, 92.5, 91.7],
        color: "#6a1b9a",
      },
      {
        name: "Black Households",
        data: [87.9, 89.3, 92.7, 86.6, 86.8],
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
          In major urban counties across New York City, most households have access to broadband internet. However, small differences emerge when looking specifically at access among Black households.
        </p>
        <p>
          In counties like Kings (Brooklyn) and Queens, access among Black households slightly exceeds or closely mirrors the countywide average. But in wealthier areas like Manhattan (New York County) and Staten Island (Richmond), Black households report lower broadband subscription rates than the county average.
        </p>
        <p>
          While the disparities may seem minor in percentages, they reflect broader systemic inequalities in housing, income, and infrastructure investment that shape digital inclusion.
        </p>
        <p>
          Let's explore how these digital access gaps may relate to opportunity in education and employment.
        </p>
      </div>
    </div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        Access to high-speed internet isn't a luxury—it's a necessity for education, job applications, remote work, and staying connected.
      </ArticleText>

      <ArticleText>
        In New York City, broadband access is generally high, with most urban counties exceeding 88% household subscription rates.
      </ArticleText>

      <ArticleText>
        But when we break it down by race, a more nuanced picture emerges. In some boroughs like Manhattan and Staten Island, Black households have noticeably lower broadband access than the general population.
      </ArticleText>

      <ArticleText>
        These gaps—though seemingly small—can represent thousands of people who are cut off from essential resources.
      </ArticleText>

      <ArticleText>
        Addressing these disparities requires more than infrastructure. It demands affordable pricing, digital literacy, and targeted local outreach.
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