<script>
export default {
scrollToTop: true,
  head () {
    return {
      title: 'THE BLOG : '+this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: this.summary },
        { hid:'og-id', 'og:title': this.title , 'og:description': this.summary, 'og:image': this.thumbnail}
      ]
    }
  },
  async asyncData({ params }) {
    const post = await import(`~/content/blog/${params.slug}.md`)
    const attr = post.attributes
    const slug = params.slug

    const {
      author,
      authorlink,
      date,
      summary,
      thumbnail,
      title,
      type,
      update
    } = attr

    const dateOptions = {
      weekday: 'long',
      year: 'numeric',
      month: 'short',
      day: 'numeric'
    }

    const publishedDate = new Date(date)
    const updatedDate = new Date(update)
    const published = publishedDate.toLocaleDateString('fr-FR', dateOptions)
    const updated = updatedDate.toLocaleDateString('fr-FR', dateOptions)

    return {
      title,
      author,
      authorlink,
      date,
      update,
      published,
      updated,
      type,
      thumbnail,
      summary,
      slug,
      html: post.html
    }
  }
}
</script>

<template>
  <section class="post">
    <div class="post-header">
      <div class="thumbnail-conteneur">
        <img v-lazy="'https://blog.donaelwalter.com'+thumbnail" class="thumbnail" :alt="title" :src="'https://blog.donaelwalter.com'+thumbnail" />
      </div>
      <div class="post-info-conteneur">
        <section class="post-type"><nuxt-link :to="`/type?type=${type}`">{{ type }}</nuxt-link></section>
        <h1 class="post-title">{{ title }}</h1>
        <p class="post-date">{{ published }}</p>
      </div>
    </div>
    <div class="post-content" v-html="html"></div>
    <div>
      <ul class="suggestion-navigation">
        <nuxt-link :to="`/`">Acceuil</nuxt-link>
        <div class="separator"></div>
        <nuxt-link :to="`/type?type=${type}`">En lire plus dans la catégorie : {{ type }}</nuxt-link>
      </ul>
    </div>
    <div class="comments">
    <h4>Commentaires</h4>
    <vue-disqus shortname="the-blog-donael-walter" :identifier="slug" :url="`https://blog.donaelwalter.com/blog/${slug}`"></vue-disqus>
    </div>                        
  </section>
</template>

<style scoped>
.post{
  margin-top: 64px;
  margin-left: 9%;
  margin-right: 9%;
  overflow-y: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.post-header{
  height: 448px;
  width: auto;
  display: flex;
  overflow: hidden;
}
.thumbnail-conteneur{
  margin-bottom: 64px;
  margin-top: 0;
  width: 55%;
  z-index: 1;
  background-color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}
.thumbnail-conteneur>img{
  width: 100%;
  height: auto;
}
.post-header>.post-info-conteneur{
  height: 100%;
  background-color: #2D70A2;
  width: 50%;
  padding:64px;
  z-index: 0;
  outline-style: solid;
  outline-color: #2D70A2;
  outline-width: 50px;
}
.post-header>.post-info-conteneur>.post-title{
  font-size: 50px;
  line-height: 57px;
  color: white;
  font-weight: bold;
  margin-bottom: 16px;
}
.post-type{
  height: 32px;
  padding: 8px;
  border-radius: 8px;
  background: rgba(0, 0, 0, 0.73);
  color: white;
  width: fit-content;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 32px;
}
.post-type>a {
  color: white;
  text-decoration :none;
}
.post-date{
  font-size: 18px;
  line-height: 21px;
  color: #BFBFBF;

}
.post-content{
  padding-top: 64px;
  margin: auto;
  margin-left: 9%;
  margin-right: 9%;
  color: white;
  overflow-y: hidden;
  margin-bottom: 64px;
  max-width: 1200px;
}
.post-content>h1,h2,h3{
  margin-top: 16px;
  margin-bottom: 16px;
}
.post-content>p{
  margin-bottom: 16px;
  width: 100%;
}
.suggestion-navigation{
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
}
.suggestion-navigation a {
  text-decoration: none;
  -webkit-text-stroke: 0.5px white;
  color: transparent;
  font-size: 2em;
}
.suggestion-navigation a:hover {
  color: white;
}
.separator{
  margin: 10px;
  height: 50px;
  width: 2px;
  background-color: white;
}
h4 {
  font-size: 3em;
  color: white;
  width: 100%;
  text-align: center;
  margin-top: 30px;
  margin-bottom: 30px;
  padding-top: 30px;
  border-top: 2px solid white;
}
.comments{
  margin: auto;
  max-width: 1000px;
  width: 100%;
}
</style>

<style>
.post-content img{
    height: auto;
    width: 50vw;
    margin: auto;
  }
  @media (max-width: 600px){
    .post-content img {
      width: 80vw;
    }
  }
.post-content>h2,h3{
  margin-top: 32px;
  margin-bottom: 16px;
}
.post-content>p{
  margin-bottom: 16px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.post-content a{
  color: rgb(132, 193, 240);
  font-weight: bold;
  text-decoration: none;
}
</style>

<style scoped>
@media (max-width: 600px) {
  .post{
    margin-left: 0%;
    margin-right: 0%;
    margin-top: 0px;
    overflow: hidden;
  }
  .post-header{
    flex-direction: column;
    height: auto;
    width: 100vw;
  }
  .thumbnail-conteneur{
    width: 100vw;
    height: 30vw;
    margin-bottom: auto;
  }
  .post-info-conteneur{
    width: 100%!important;
  }
  .post-content{
    margin-right: 3%;
    margin-left: 3%;
  }
  .post-title{
    font-size: 2em!important;
  }
  .comments{
   padding: 3%;
  }
  .suggestion-navigation{
    flex-direction: column;
  }
  .separator{
    height: 2px;
    width: 50px;
  }
  .suggestion-navigation>a{
    text-align: center;
  }
}
</style>