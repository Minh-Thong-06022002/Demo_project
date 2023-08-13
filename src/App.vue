<template>
  <ul></ul>
</template>

<script>
export default {
  data() {
    return {
      storedResources: [
        {
          id: 'offical guide',
          title: 'Offical Guide',
          description: 'The Official Vus JS Documentation',
          link: 'http://vuejs.org',
        },
        {
          id: 'Google',
          title: 'Google Chrome',
          description: 'Learn to Google',
          link: 'http://google.org',
        }
      ], 
    }
  },
}
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
