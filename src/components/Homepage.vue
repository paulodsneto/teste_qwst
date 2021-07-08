<template>
    <div>
        <h2>Homepage</h2>
        <div v-for="story in stories" :key="story">
            <h2> {{story.data.title}}</h2>
            <p>{{story.data.url}}</p>
            <p>Comments: {{story.data.descendants}}</p>
            <p>Score: {{story.data.score}}</p>
        </div>    
    </div>    
</template>

<script>
import axios from 'axios'

export default {
    name: 'Homepage',
    data: function (){
        return {
            err: '',
            stories: []
        }
    },
    created: function (){
        // https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty
        axios.get('https://hacker-news.firebaseio.com/v0/topstories.json')
        .then((Response)=>{
            let results = Response.data.slice(0, 10)
            results.forEach(id => {
                axios.get('https://hacker-news.firebaseio.com/v0/item/' + id + '.json')
                .then((Response => {
                    this.stories.push(Response)
                }))
            })  
        })
        .catch((err)=> {
            this.err = err
        })
    }
}
</script>

<style scoped>

</style>