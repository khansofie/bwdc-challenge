<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
  <Scroller layout="right">
    {#snippet scrolly()}
      <ArticleText>
        Education is one of the most powerful tools for social and economic mobility. 
        But not all groups have equal access to higher education.
      </ArticleText>

      <ArticleText>
        We've seen how degree attainment varies widely across racial and ethnic groups, 
        shaping the foundation for future job opportunities.
      </ArticleText>

      <ArticleText>
        Those disparities continue into the job market. Even with a STEM degree, 
        some groups face more barriers to finding employment in their field.
      </ArticleText>

      <ArticleText>
        And it doesn't stop there — access to something as basic as high-speed internet 
        can drastically impact education, job access, and daily life.
      </ArticleText>

      <ArticleText>
        Our data from New York City counties showed that broadband and high-speed internet 
        usage vary by race and geography, reinforcing inequalities that start early 
        and ripple across generations.
      </ArticleText>

      <ArticleText>
        <strong>These issues are connected.</strong> From education to employment to digital infrastructure,
        the path to opportunity isn't equally paved.
      </ArticleText>

      <ArticleText>
        <strong>So what’s next?</strong> A more equitable future is possible — but only if we work for it.
      </ArticleText>

      <ArticleText>
        Whether it’s supporting policies that expand broadband access, investing in underserved communities, 
        or rethinking how we support students from underrepresented backgrounds — small actions add up.
      </ArticleText>

      <ArticleText>
        <strong>Take action, stay informed, and use your voice.</strong> Real change happens when we all get involved.
      </ArticleText>
    {/snippet}
  </Scroller>
</div>

<style>
  .article-text {
    color: white;
    font-size: 1.1em;
    line-height: 1.6;
    max-width: 600px;
    margin: 0 auto;
  }
</style>