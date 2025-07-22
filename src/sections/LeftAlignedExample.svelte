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
      color: "#000080",
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
      color: "#ffa500",
    },
  ];

  let chart;
  let visible = {
    Asian: true,
    Black: true,
    Hispanic: true,
    White: true,
  };

  let options = {
    chart: {
      type: "spline",
      backgroundColor: "#ff99fc",
      borderColor: "#d0ddda",
      borderWidth: 5,
      borderRadius: 20,
      marginTop: 80,
    },
    title: {
      text: "STEM vs. non-STEM Employment Rates Among 25-34 Year Olds with a STEM Degree",
    },
    subtitle: {
      text: "Nationwide",
    },
    yAxis: {
      min: 0,
      max: 15,
      title: {
        text: "Percentage of People (%)",
      },
    },
    series: series.filter(s => visible[s.name]),
  };

  function toggleSeries(name) {
    visible[name] = !visible[name];

    if (visible[name]) {
      chart.addSeries(series.find(s => s.name === name));
    } else {
      const existingSeries = chart.series.find(s => s.name === name);
      if (existingSeries) existingSeries.remove();
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

      <div class="buttons">
        {#each Object.keys(visible) as group}
          <button class="toggle-button" on:click={() => toggleSeries(group)}>
            {visible[group] ? `Remove ${group}` : `Add ${group}`}
          </button>
        {/each}
      </div>

      <div class="explanation">
        <p>
          This graph compares employment rates among 25-34 year olds with a STEM degree across different racial and ethnic groups in the United States.
        </p>
        <p>
          Notice that Asian and Black groups have a higher rate of employment in STEM fields compared to Hispanic and White groups, 
          but all groups see a decline from 2016 to 2023. These trends highlight ongoing disparities and challenges in the STEM job market, highlighting the need for targeted support and opportunities.
        </p>
        <p>
          As you scroll, we'll explore how access to resources like reliable internet connection can influence these employment outcomes.
        </p>
      </div>
    </div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        STEM degrees often open doors to higher-paying and in-demand jobs. But how do employment rates compare across different racial and ethnic groups?
      </ArticleText>

      <ArticleText>
        This graph tracks employment rates in STEM vs. non-STEM jobs among 25 to 34-year-olds 
        with STEM degrees, comparing four major racial and ethnic groups from 2016 to 2023.
      </ArticleText>

      <ArticleText>
        While employment rates have generally declined across all four of these groups, Asian graduates maintain the 
        highest employment rate, followed by Black, Hispanic, and White graduates.
      </ArticleText>

      <ArticleText>
        The decline for each group signals potential challenges in the job market, but the gaps between groups highlight persistent disparities.
      </ArticleText>

      <ArticleText>
        What factors might contribute to these gaps? Access to networks, discrimination, geographic distribution, or differences in STEM fields pursued.
      </ArticleText>

      <ArticleText>
        Understanding these trends help us explore what can be done to improve employment outcomes for all STEM graduates. Let's look at this more critically.
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .chart {
    padding-top: 40px;
    width: 600px;
    max-width: 90vw;
    margin: 0 auto;
    padding-bottom: 40px;
  }

  .buttons {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 12px;
    margin: 20px auto;
    max-width: 600px;
  }

  .toggle-button {
    padding: 15px 30px;
    color: #ffffff;
    background-color: #ff99fc;
    border: solid 2px #d0ddda;
    border-radius: 16px;
    font-size: large;
    cursor: pointer;
    transition: all 0.2s ease;
    box-shadow: 0 4px 0 #d0ddda;
  }

  .toggle-button:active {
    transform: translateY(2px);
    box-shadow: 0 2px 0 #d0ddda;
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
   /*font-family: serif;*/
  }
</style>