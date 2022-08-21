<script setup>
const route = useRoute()
</script>

<template>
  <div>
    <div>
      <p>The current route is: {{ route.fullPath }}</p>
      <p>
        <a href="/api/hello">Go to /api/hello</a>
      </p>
    </div>

    <div>
      <h2>Description:</h2>
      <p>The route above should never reach <code>/api/hello</code>.</p>
      <p>
        However, when we run <code>nuxt dev</code>, then create
        <code>server/api/hello.ts</code> after (and only after, including parent
        directories), we see that the new server route is not automatically
        detected (this root page will be loaded instead). The new server route
        is only detected after we manually restart the development server.
      </p>
    </div>
  </div>
</template>

<style>
body {
  font-family: system-ui;
  max-width: 30rem;
  margin: 0 auto;
  padding-top: 2rem;
}
</style>
