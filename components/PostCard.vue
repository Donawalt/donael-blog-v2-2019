<template>
    <article class="article-card">
       <nuxt-link :to="`/blog/${$attrs.postinfo.link}`">
       <div class="featured-conteneur">
                 <img class="featured-image" :v-lazy="'https://blog.donaelwalter.com'+`${$attrs.postinfo.attributes.thumbnail}`" :src="'https://blog.donaelwalter.com'+`${$attrs.postinfo.attributes.thumbnail}`" loading="lazy"/>

       </div>
        <div class="article-info">
          <p class="article-type">{{$attrs.postinfo.attributes.type}}</p>
          <h5 class="article-title">{{$attrs.postinfo.attributes.title}}</h5>
          <p class="article-author">by {{$attrs.postinfo.attributes.author}}</p>
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
    text-decoration: none;
  }
  .featured-conteneur{
    height: 150px;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .article-card:hover .featured-image{
    transform: scale(1.05);
    transition: 500ms;
  }
  .featured-image{
    width: 256px;
    margin-right: 32px;
    transition: 200ms;
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