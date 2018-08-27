<template>
    <div id="post">
        <div class="post-thumbnail">
        </div>    
        <h1>{{title}}</h1>
        <p>{{content}}</p>
    </div>
</template>
<script>
export default {
    asyncData(context) {
        return context.app.$storyapi.get('cdn/stories',{
            version: 'draft',
            starts_with: 'blog/'
        }).then(res=>{
            console.log(res)
            // return{
            //     title: res.data.story.content.title,
            //     excerpt: res.data.story.content.excerpt,
            //     content: res.data.story.content.content,
            //     thumbnail: res.data.stry.content.thumbnail,

            // }
        })
    }
}
</script>
<style scoped>
/* #id {

}
.post-thumbnail {

} */
</style>
