<template>
  <section>
    <section class="header-title">
      <h1>The Blog</h1>
      <p>by <b>DONAËL WALTER</b></p>
    </section>
    <section class="content">
      <div class="last">
        <MainCard 
        :postinfo="blogList[blogList.length -1]"
        />
      </div>
      <div class="list">
        <p class="list-title">Recent articles</p>
        <PostCard
        v-for="(blog, index) in blogList"
        :key="index"
        :attributes="blog.attributes"
        :postinfo="blog"
        />
      </div>
    </section>
  </section>
</template>

<script>
// pages/index.vue
import blogs from '~/content/blogs.json'
import PostCard from '~/components/PostCard'
import MainCard from '~/components/MainCard'

export default {
  scrollToTop: true,
  head () {
    return {
      title: 'THE BLOG by Donaël WALTER',
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: this.summary },
        { hid:'og-id', 'og:title': 'THE BLOG', 'og:description': 'Test description'}
      ]
    }
  },
  components: {
    PostCard,
    MainCard
  },
  async asyncData({ app }) {
    async function awaitImport(blog) {
      const wholeMD = await import(`~/content/blog/${blog.slug}.md`)
      return {
        attributes: wholeMD.attributes,
        link: blog.slug
      }
    }

    const blogList = await Promise.all(
      blogs.map(blog => awaitImport(blog))
    ).then(res => {
      return {
        blogList: res
      }
    })
    return blogList
  }
}
</script>

<style  scoped>
  h1{
    font-size: 100px;
    text-transform: uppercase;
    color: white;
    font-weight: bold;
    text-align: center;
  }
  h1+p{
    font-size: 20px;
    color: white;
    text-align: center;
  }
  .header-title{
    height: 112px;
    margin-top: 64px;
    margin-bottom: 64px;
  }
  .content{
    margin-left: 9%;
    margin-right: 9%;
    margin: auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    max-width: 1200px;
  }
  .last{
    margin-right: 32px;
  }
  .list-title{
    height:18px;
    font-weight: bold;
    font-size: 17px;
    color: white;
    margin-bottom: 16px;
  }
  .list{
    margin-left:32px;
  }
</style>