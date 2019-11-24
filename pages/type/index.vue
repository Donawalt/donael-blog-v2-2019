<template>
  <section>
    <section class="header-title">
      <h1>{{this.type}}</h1>
      <p> Articles par <b>DONAËL WALTER</b></p>
    </section>
    <section class="content">
      <div class="list">
        <MainCard
        v-for="(blog, index) in sortedArticle"
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
  head () {
    return {
      type : this.$route.query.route,
      title: 'THE BLOG by Donaël WALTER'+ ''+ this.$route.query.type,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: this.summary },
        { hid:'og-id', 'og:title': 'THE BLOG', 'og:description': 'Test description'}
      ]
    }
  },
  data(){
    return {
      type : 'default'
    }
  },
  created(){
    this.type = this.$route.query.type
  },
  components: {
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
  },
  computed :{
      sortedArticle(){
            return this.blogList.filter(blog => blog.attributes.type == this.type);
      }
  },
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
    margin-bottom: 10%;
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
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 2%;
  }
</style>