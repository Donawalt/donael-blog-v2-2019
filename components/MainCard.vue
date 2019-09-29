<template>
    <article class="article-card">
       <nuxt-link :to="`/blog/${$attrs.postinfo.link}`">
        <section>
          <img class="featured-image" :src="`${$attrs.postinfo.attributes.thumbnail}`"/>
          <p class="article-type">{{$attrs.postinfo.attributes.type}}</p>
        </section>
        <div class="article-info">
          <small>{{$attrs.postinfo.attributes.date}}</small>
          <h5 class="article-title">{{$attrs.postinfo.attributes.title}}</h5>
          <p class="article-author">by {{$attrs.postinfo.attributes.author}}</p>
          <p>{{$attrs.postinfo.attributes.resume}}</p>
        </div>
       </nuxt-link>
    </article>
</template>

<script>
export default {
    props: {
    articleInfo: {
      type: Object,
      default: () => {}
    },
    index: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped>
  .article-card{
    margin-bottom: 32px;
    display: flex;
  }
  a{
    display: flex;
  }
  .featured-image{
    width: 256px;
    margin-right: 32px;
  }
  .article-type{
    font-size:12px;
    color: rgb(21, 255, 0);
    text-transform: uppercase;
    font-weight: bold;
    margin-bottom: 16px;
  }
  .article-title{
    font-size: 20px;
    color: white;
    font-weight: bold;
    margin-bottom: 8px;
  }
  .article-author{
    font-size: 12px;
    color: #AAAA;
    font-weight: bold;
  }
</style>