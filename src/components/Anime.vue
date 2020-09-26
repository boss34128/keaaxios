<template>
  <div>
    <div class="mt-3">
      <input type="text" v-model="keyword" class="button-s" />
      <button @click="searchData()" class="button-a" id="green">Search</button>
    </div>

    <div class="mt-4">
      <b-card-group columns>

        <b-card no-body class="shee" style="max-width: 600px" v-for="sound in music"
                :key="sound.trackId">

          <b-row no-gutters>
            <b-col md="3">
              <b-card-img
                :src="sound.artworkUrl100"
                :alt="sound.name"
                class="rounded-0 mt-4 ml-2"
              ></b-card-img>
            </b-col>
            <b-col md="8">
              <b-card-body class="ml-3">
                <b-card-title :title="sound.trackName" class="chee">
                  
                </b-card-title>
                <b-card-text>
                  {{ sound.artistName }}<br />
                  <audio controls style="max-width: 20rem">
                    <source :src="sound.previewUrl" type="audio/mpeg" />
                  </audio>
                </b-card-text>
              </b-card-body>
            </b-col>
          </b-row>
        </b-card>
      </b-card-group>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      music: null,
      keyword: "",
    };
  },

  methods: {
    searchData() {
      console.log(this.keyword);
      axios
        .get(
          "https://itunes.apple.com/search?term=" + this.keyword + "&limit=3"
        )

        .then((response) => {
          this.music = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
.button-s {
  background-color: rgb(190, 218, 243);
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 4px 2px;
  font-size: 30px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid white;
}
.button-a {
  background-color: rgb(160, 207, 248);
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 4px 2px;
  font-size: 30px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid white;
  width: 110px;
}
button:hover#green {
  color: #2c07ff;
}
.shee {
  background-color: rgba(0, 0, 0, 0.5);
  color: rgb(255, 255, 255);
  border: none;
  padding: 5px 5px 5px 5px;
  margin: 4px 2px;
  border-radius: 10px;
  border: 0.5px solid rgb(0, 0, 0);
  width: 110px;
}
.chee {
  font-size: 22px;
}
</style>