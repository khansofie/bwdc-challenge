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

  // Track visibility for each group
  let visible = {
    Asian: true,
    Black: true,
    Hispanic: false,
    White: false,
  };

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
    // Initially only Asian and Black visible
    series: [series.find(s => s.name === "Asian"), series.find(s => s.name === "Black")],
  };

  function toggleSeries(seriesName) {
    if (!chart) return;

    const existingSeries = chart.series.find(s => s.name === seriesName);

    if (existingSeries) {
      existingSeries.remove();
      visible[seriesName] = false;
    } else {
      const newSeries = series.find(s => s.name === seriesName);
      if (newSeries) {
        chart.addSeries(newSeries);
        visible[seriesName] = true;
      }
    }
  }
</script>

<div>
  <Scroller layout="center">
    {#snippet sticky()}
      <div class="sticky-container">
        <div class="chart">
          <Chart bind:chart {options} Highcharts={Highcharts} />
        </div>

        <div class="buttons">
          {#each Object.keys(visible) as group}
            <button class="toggle-button" on:click={() => toggleSeries(group)}>
              {visible[group] ? `Remove ${group}` : `Add ${group}`}
            </button>
          {/each}
        </div>

        <div class="explanation">
          <p>You can use Svelte to add and remove data from a Highcharts chart.</p>
          <p>Click the buttons above to toggle each racial/ethnic group.</p>
          <p>
            <strong>🤔 How might you use other HTML elements, like checkboxes or radio buttons, in a similar way to filter data?</strong>
          </p>
        </div>
      </div>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>
        STEM degrees are a path to high-paying jobs and a financially stable life ahead. But the question is who's actually getting those jobs, and are they working in their field?
      </ArticleText>

      <ArticleText>
        The graph shows the current employment rates for STEM vs non-STEM jobs.
      </ArticleText>

      <ArticleText>
        You might also want to add more interactivity or gamify parts of your scrollytelling piece.
      </ArticleText>

      <ArticleText>
        <strong>It's up to you to research how to create the effects and functionality that you envision!</strong>
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

  .buttons {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    margin: 20px 0;
  }

  .toggle-button {
    padding: 15px 25px;
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