<template>
    <div>
        <div v-for="story in stories" :key="story">
            <table style="width:100%">
                <tr>
                    <th><strong><a :href="story.data.url" target="_blank" rel="noopener" style="text-decoration:none;">{{ story.data.title }}</a></strong> ({{ story.data.by }})</th>
                </tr>
            </table>
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
            // https://hacker-news.firebaseio.com/v0/newstories.json
            axios.get('https://hacker-news.firebaseio.com/v0/newstories.json')
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