<template>
<div>
    <div class="searchSpace">
        <input size="40" v-model="keyword" placeholder="検索キーワードを入力">
        <button @click="search_video">Search</button>
    </div>
    <table cellspacing="0" cellpadding="5" v-show="results">
        <tr class="tableHead">
            <th width="50">
                <font>No</font>
            </th>
            <th width="200">
                <font>Video</font>
            </th>
            <th width="700">
                <font>Content</font>
            </th>
        </tr>

        <tr class="tableContents" v-for="(movie, index) in results" v-bind:key="movie.id.videoId">
            <!-- No -->
            <td valign="top" width="5%">{{ index + 1 }}</td>
            <!-- Video -->
            <td valign="top" width="55%">
                <a v-bind:href="'https://www.youtube.com/watch?v=' + movie.id.videoId">
                    <img v-bind:src="movie.snippet.thumbnails.medium.url">
                </a>
            </td>
            <!-- title description -->
            <td align="left" valign="top" width="40%">
                <font size="5" color="#8373f5"><b>{{ movie.snippet.title }}</b></font>
                <br>
                {{ movie.snippet.description }}
            </td>
        </tr>
    </table>    
</div>
</template>

<script>
import axios from 'axios'

export default {
    name: "SearchVideo",
    data: function() {
        return {
            results: null,
            keyword: "マーベル",
            order: "viewCount",
            params: {
                q: "",
                part: "snippet",
                type: "video",
                maxResults: "20",
                key: "AIzaSyDgOORLDK9GBMKiiAb8ND4jE2I4ol3ghuY"
            }
        };
    },
    props: {
        msg: String
    },
    methods: {
        search_video: function() {
            this.params.q = this.keyword;
            var self = this;
            axios
              .get("https://www.googleapis.com/youtube/v3/search", {
                params: this.params
              })
              .then(function(res) {
                self.results = res.data.items;
              })
        }
    }
};
</script>

<style>

.searchSpace {
    background-color: #051474;
    padding: 50px;
}

input {
    border: 1px solid #999;
    padding: 3px 10px;
    border-radius: 3px;
    height: 2.2em;
    overflow: hidden;
}

button {
    cursor: pointer;
    font-size: 1.2em;
    border: none;
    background: #8373f5;
    border-radius: 3px;
    color: #fff;
    outline : none;
    width: 4em;
    height: 1.9em;
    display: inline-block;
    vertical-align: middle;
    margin-left: 20px;
}

table {
    width: 100%;
    border-collapse: collapse;
    border: solid 2px #8373f5;
}

table th {
    color: #fff0f5;
    background: rgb(35, 9, 115);
    border: dashed 1px #8373f5;
}

table td {
    background: #fff0f5;
    border: dashed 1px #8373f5;
}

@media screen and (max-width: 768px) {
   input {
    width: 70%;
   }

   button {
    width: 30%;
    margin-top: 20px;
   }

    .tableHead th:nth-child(3) {
        display: none;
    }

    .tableContents td:nth-child(3) {
        display: none;
    }
}

</style>