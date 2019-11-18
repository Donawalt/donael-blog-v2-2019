<template>
    <article class="article-card">
       <nuxt-link :to="`/blog/${$attrs.postinfo.link}`">
        <section class="thumbnail">
          <div class="thumbnail-container">
            <img class="featured-image" :src="`${$attrs.postinfo.attributes.thumbnail}`" loading="lazy"/>
          </div>
          <p class="article-type"><nuxt-link :to="`/type?type=${$attrs.postinfo.attributes.type}`">{{$attrs.postinfo.attributes.type}}</nuxt-link></p>
        </section>
        <div class="article-info">
          <h5 class="article-title">{{$attrs.postinfo.attributes.title}}</h5>
          <small class="article-date">{{$attrs.postinfo.attributes.date}}</small>
          <p class="article-author">by {{$attrs.postinfo.attributes.author}}</p>
          <p class="article-summary">{{$attrs.postinfo.attributes.summary}}</p>
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
  .thumbnail{
    position: relative;
  }
  .article-card{
    margin-bottom: 32px;
    background-color: #2D70A2;
    padding-bottom: 32px;
    border-radius: 8px;
    overflow: hidden;
    transition: 500ms;
  }
  .article-card:hover .featured-image{
    transform: scale(1.05);
    transition: 500ms;
  }
  a{
    text-decoration: none;
  }
  .thumbnail-container{
    max-width: 608px;
    height: 320px;
    width: 100%;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .featured-image{
    width: 105%;
    transition: 200ms;
  }
  .article-type{
    height: 32px;
    padding: 8px;
    border-radius: 8px;
    background: rgba(0, 0, 0, 0.73);
    color: white;
    width: fit-content;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 32px;
    margin-bottom: 32px;
    position: absolute;
    bottom: 0;
  }
  .article-type>a{
    color: white;
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
    margin-top: 8px;
    margin-bottom: 16px;
  }
  .article-info {
    margin: 32px;
  }
  .article-summary{
    font-size: 17px;
    text-decoration: none;
    color: white;
  }
  .article-date{
    margin-bottom:16px;
    color: azure;
  }
</style>