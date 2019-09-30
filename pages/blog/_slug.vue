<script>
export default {
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
        <img v-lazy="thumbnail" class="thumbnail" :alt="title" />
      </div>
      <div class="post-info-conteneur">
        <section class="post-type">{{ type }}</section>
        <h1 class="post-title">{{ title }}</h1>
        <p class="post-date">{{ published }}</p>
      </div>
    </div>
    <div class="post-content" v-html="html"></div>
  </section>
</template>

<style scoped>
.post{
  margin-top: 64px;
  margin-left: 9%;
  margin-right: 9%;
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
.post-date{
  font-size: 18px;
  line-height: 21px;
  color: #BFBFBF;

}
.post-content{
  margin-top: 64px;
  margin-left: 9%;
  margin-right: 9%;
  width: 100%;
}
</style>