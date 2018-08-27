<template>
  <section class="container">
    <PostPreview
    v-for="post in posts"
    :key="post.id"
    :title="post.title"
    :excerpt="post.previewText"
    :thumbnailImage="post.thumbnailUrl"
    :id="post.id"
    ></PostPreview>

  </section>
</template>

<script>
import PostPreview from "~/components/Blog/index.vue"
export default {
  components:{
    PostPreview
  },
  asyncData(context) {
    return context.app.$storyapi
      .get('cdn/stories', {
        version: 'draft',
        starts_with: 'blog/'
      })
      .then(res => {
        return{ 
          posts: res.data.stories.map(bp => {
            return {
              id: bp.slug,
              title :bp.content.title,
              previewText: bp.content.excerpt,
              thumbnailUrl: bp.content.thumbnail,
            }
          })
        }
      })
    }
  // data() {
  //   return{
  //     posts :[{
  //       title: 'a begining',
  //       previewText: 'this is just a test',
  //       thumbnailUrl: 'http://wall2born.com/data/out/308/image-45315079-nice-desktop-backgrounds-hd.jpg',
  //       id:'an-simlpe-id' 
  //     },
  //     {
  //       title: 'another',
  //       previewText: 'this is just another',
  //       thumbnailUrl: 'http://wall2born.com/data/out/308/image-45315079-nice-desktop-backgrounds-hd.jpg',
  //       id:'an-simlpe-id1'
  //     },
  //     ]
  //   }
  // }
}
</script>

<style scoped>
.container{
  padding-top: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  
}
@media (min-width: 35rem){
  .container{
    display: flex;
    flex-direction: row
  }

}

</style>
