<template>
    <div>
        <center>
        <input type="text" v-model="search" placeholder="Search Hacker News..." />
        <div v-for="story in filteredNews" :key="story">
        <article><strong><a :href="story.data.url" target="_blank" rel="noopener" style="text-decoration:none;">{{ story.data.title | to-uppercase }}</a></strong> 
           ({{ story.data.by | snippet }})</article>
        </div>

        </center>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {

        name: 'Homepage',
        data:  function () {
            return {
                err: '',
                stories: [],
                search: ""
            }
        },
        created: function () {
            // https://hacker-news.firebaseio.com/v0/newstories.json
            axios.get('https://hacker-news.firebaseio.com/v0/newstories.json')
                .then((response) => {
                    let results = response.data.slice(0, 50)
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
        },
        computed: {
            filteredNews: function(){
                return this.stories.filter((story) => {
                    return story.data.title.match(this.search);
                });
            }
        }
    }
</script>

<style scoped>
article{
    display: table;
    border-collapse:  separate;
    border-spacing: 3px;
    width: 100%;
}
    
    input {
        margin: 50%, 50% auto;
        width: 300px;
        padding: 4px;
        margin-top: 2px;
        font-size: 14px;
    }
    
    input[type=text] {
        text-align: center;
        -webkit-transition: width 0.4s ease-in-out;
        transition: width 0.4s ease-in-out;
    }
    
    input[type=text]:focus {
        width: 50%;
    }

</style>