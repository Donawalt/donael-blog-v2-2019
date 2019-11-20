<template>
    <div class="content">
      <div class="nav-container">
        Section du site en construction sorry !
      <!-- <nav class="nav">
        <nuxt-link :to="`/type?type=${blog.attributes.type}`" v-for="blog in filterType" :key="blog">{{blog.attributes.type}}</nuxt-link>
      </nav>-->
      </div>
    </div>
</template>

<script>
import blogs from '~/content/blogs.json'

export default {
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
    console.log(blogList);
    return blogList
  },
  created(){
       this.distinctValue = [...new Set(this.blogList)];
  },
  mounted : function(){
  },
  computed: {
      filterType(){
          return this.distinctValue
      }
  }
} 
</script>
<style scoped>
.content{
    height: 50vh;
    display: flex;
    justify-content: center;
    align-items: center;
    display: flex;
      justify-content: start;
  align-items: flex-start;
}
a{
  text-decoration: none;
  color: white;
  list-style: none;;
  transform-style: preserve-3d;
  font-family: condor-compressed,sans-serif;
  line-height: 1em;
  font-weight: 700;
  text-transform: uppercase;
  font-size: 10vw;
  margin-left: 1%;
  margin-right: 1%;
}
.nav-container{
  position: absolute;
    left: 50%;
    top: 50%;
    -webkit-align-self: center;
    -ms-flex-item-align: center;
    -ms-grid-row-align: center;
    align-self: center;
    perspective: 1000px;
    -webkit-transform: translate(-50%,-50%);
    -ms-transform: translate(-50%,-50%);
    transform: translate(-50%,-50%);
    display: flex;
    justify-content: center;
    align-items: center;
}
nav{
  position: relative;
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: center;
    -webkit-justify-content: center;
    -ms-flex-pack: center;
    justify-content: center;
    -webkit-box-align: center;
    -webkit-align-items: center;
    -ms-flex-align: center;
    align-items: center;
    perspective: 1000px;
}

.error-message{
    font-size: 20px;
    color: white;
}
</style>