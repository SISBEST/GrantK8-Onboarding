<template>
  <div class="container">
    <div>
      <h1 class="title">
        {{ article.title }}
      </h1>
      <p>
        {{ article.body }}
      </p>
    </div>
    <div>
    <a
          :href="next"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Next
        </a>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const article = await $content('lessons', params.slug).fetch()
    const next = '/learn/' + (parseInt(article.sid + 1, 10))
    return { article, next }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
