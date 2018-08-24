<template>
    <nuxt-link
    :to="id"
    >
        <article class="post-preview">
            <div class="post-preview-thumbnail"
            :style="{backgroundImage: 'url('+ thumbnailImage+')'}"
            ></div>
            <div class="post-preview-text">
                <h2>{{title}}</h2> 
                <p>{{excerpt}}</p>
            </div>
        </article>
    </nuxt-link>

</template>
<script>
export default {
    props:{
        title: {
            type: String,
            required: true
        },
        excerpt: {
            type: String,
            required: true,
        },
        thumbnailImage:{
            type: String,
            required: true,
        },
        id: {
            type: String,
            required: true,
        }

    }
}
</script>
<style scoped>
a {
    text-decoration: none;
    color:black;
}
.post-preview {
    border-radius: 3px;
    box-shadow: 1px 1px 5px grey;
    width: 90%;
    margin: auto;
    height: 20rem;
    margin: 1rem;
}
.post-preview-thumbnail {
    background-position: center;
    background-size: cover;
    width: 100%;
    height: 10rem;
}
.post-preview-text {
    text-align: center;
    padding: 1rem;
}
@media (min-width: 35rem) {
    .post-preview {
        width: 25rem;
    }
}
</style>

