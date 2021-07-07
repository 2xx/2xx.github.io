<template>
  <Layout>
    <div>
      <h1>{{ $page.post.title }}</h1>
      <div>{{ $page.post.content }}</div>
    </div>
  </Layout>
</template>

<page-query>
query ($id: ID!) {
  post (id: $id) {
    id
    title
    content
  }
}
</page-query>

<script>
import MarkdownIt from 'markdown-it'
const md = new MarkdownIt();
// var result = md.render('# hell');

export default {
  name: 'PostPage',
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  },
  methods:{
      mdToHtml(markdown) {
          return md.render(markdown);
      }
  } 
  // metaInfo: {
  //   title: ''
  // }
}
</script>

<style>

</style>
