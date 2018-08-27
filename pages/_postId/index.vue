<template>
    <div id="post">
        <div class="post-thumbnail" :style="{backgroundImage: 'url('+thumbnail+')'}">
        </div>
        <div class="post-content">  
            <h1>{{title}}</h1>
            <p>{{content}}</p>
        </div>
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
            return{
                title: res.data.stories[0].content.title,
                excerpt: res.data.stories[0].content.excerpt,
                content: res.data.stories[0].content.content,
                thumbnail: res.data.stories[0].content.thumbnail,

            }
        })
    }
}
</script>
<style >
#post {
    white-space: pre-line;
}
.post-content {
    width: 500px;
    max-width: 80%;
    margin: auto;
}
.post-thumbnail {
    width: 100%;
    height: 300px;
    background-size: cover;
    background-position: center;
}
</style>
