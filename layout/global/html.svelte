<script>
  import Head from './head.svelte';

  export let route, content, allContent;
</script>

<html lang="en">
<Head title={content.filename} />
<body>
  <section>
    <svelte:component this={route} {...content.fields} {allContent} />
  </section>
</body>
</html>

<style>
  section {
    max-width: 1200px;
    margin: 0 auto;
  }
</style>