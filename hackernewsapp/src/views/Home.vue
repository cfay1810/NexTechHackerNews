<template>
    <div>
        <h2>Hacker News</h2>        
        <div v-for="story in stories" :key="story">
            <h3>{{ story.data.title }} | Author: {{ story.data.by }}</h3>
            <p>{{ story.data.url }}</p>
            </div>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {

        name: 'Homepage',
        data:  function () {
            return {
                err: '',
                stories: []
            }
        },
        created: function () {
            // https://hacker-news.firebaseio.com/v0/topstories.json
            axios.get('https://hacker-news.firebaseio.com/v0/topstories.json')
                .then((response) => {
                    let results = response.data.slice(0, 10)
                    results.forEach(id => {
                        axios.get('https://hacker-news.firebaseio.com/v0/item/' + id + '.json')
                            .then((response) => {
                                this.stories.push(response)
                            })
                            .catch((err) => {
                                this.err = err
                            })
                    })
                })
                .catch((err) => {
                    this.err = err
                })
        }
    }
</script>

<style scoped>
</style>