<template>
<div>
    <div><font size="6" color="#c71585">YouTube Search list (Vue.js CLI)</font></div>
    <br>
    <input size="40" placeholder="検索キーワードを入力">
    <button>検索</button>
    <table cellspacing="0" cellpadding="5">
        <tr>
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

        <tr>
            <!-- No -->
            <td valign="top" width="50"></td>
            <!-- Video -->
            <td valign="top" width="300">
                <a href="'https://www.youtube.com/watch?v=' + movie.id.videoId">
                    <img width="300" height="200" src="movie.snippet.thumbnails.medium.url">
                </a>
            </td>
            <!-- title description -->
            <td align="left" valign="top" width="700">
                <font size="5" color="#c71585"><b>{{ movie.snippet.title }}</b></font>
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
            keyword: "marvel",
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

table {
    border-collapse: collapse;
    border: solid 2px #c71585;
}

table th {
    color: #fff0f5;
    background: #ff69b4;
    border: dashed 1px #c71585;
}

table td {
    background: #fff0f5;
    border: dashed 1px #c71585    
}

</style>