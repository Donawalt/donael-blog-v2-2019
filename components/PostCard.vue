<template>
    <article class="article-card">
       <nuxt-link :to="`/blog/${$attrs.postinfo.link}`">
       <div class="featured-conteneur">
                 <img class="featured-image" :v-lazy="'https://blog.donaelwalter.com'+`${$attrs.postinfo.attributes.thumbnail}`" :src="'https://blog.donaelwalter.com'+`${$attrs.postinfo.attributes.thumbnail}`" loading="lazy"/>
       </div>
       </nuxt-link>
       <div class="article-info">
          <p class="article-type"><nuxt-link :to="`/type?type=${$attrs.postinfo.attributes.type}`">{{$attrs.postinfo.attributes.type}}</nuxt-link></p>
          <h5 class="article-title"><nuxt-link :to="`/blog/${$attrs.postinfo.link}`">{{$attrs.postinfo.attributes.title}}</nuxt-link></h5>
          <p class="article-author">by {{$attrs.postinfo.attributes.author}}</p>
        </div>
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
  .article-type>a{
    font-size:12px;
    color: rgb(21, 255, 0);
    text-transform: uppercase;
    font-weight: bold;
    margin-bottom: 16px;
  }
  .article-title>a{
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
<style scoped>
@media (max-width: 600px){
  .article-card{
    width: 100%;
    padding-left: 3%;
    padding-right: 3%;
    flex-direction: column;
    overflow: hidden;
  }
  .featured-conteneur{
    overflow: hidden;
    text-align: center;
    display: block;
    position: relative;
    width: 100%;
  }
  .featured-image{
    margin: auto;
    width: 100%;
    position: absolute;
    bottom: 50%;
    transform: translate(-50%,50%);
  }
  .article-card:hover .featured-image{
    transform: translate(-50%,50%) scale(1.1);
  }
}
</style>