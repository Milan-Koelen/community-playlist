<script setup></script>

<template>
  <div
    class="
      mx-16
      lg:ml-[-20%] lg:mr-[15%] lg:px-[25vw]
      xl:mr-[25%]
      py-[33vh]
      md:px-[15vw]
    "
  >
    <div
      class="
        bg-[rgba(100,100,100,.30)]
        backdrop-blur-lg
        rounded-lg
        px-6
        py-4
        border-2 border-gray-600 border-opacity-25
      "
    >
      <div>
        <h1
          class="
            text-orange-600
            font-bold
            drop-shadow-lg
            tracking-wide
            text-3xl
            my-1
          "
        >
          Community Radio
        </h1>
        <p class="flex text-slate-200 drop-shadow-lg">
          Add your favorite tracks below, sepparated by commas...
        </p>
        <form @submit="submitTrack">
          <input
            style="text-align: center"
            type="text"
            @keydown="keydown"
            v-model="trackUrl"
            placeholder="YouTube or SoundCloud link here"
            class="h-12 mt-3 rounded-lg text-slate-600 w-full caret-transparent"
            name="track"
            autofocus
          />
          <div class="flex justify-around">
            <button
              class="
                align-self-end
                bg-orange-600
                text-white
                hover:bg-orange-500
                px-5
                text-lg text-align-center
                font-semibold
                rounded-lg
                py-2
                mt-5
                mb-3
              "
              @click.prevent="submitTrack()"
            >
              Add Track
            </button>
            <button
              class="
                align-self-end
                bg-orange-600
                text-white
                hover:bg-orange-500
                px-5
                text-lg text-align-center
                font-semibold
                rounded-lg
                py-2
                mt-5
                mb-3
              "
              @click.prevent="playMusic()"
            >
              Play music
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
  <audio autoplay src="http://localhost:4000/">
    Your browser does not support the
    <code>audio</code> element.
  </audio>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      trackUrl: "",
    };
  },
  methods: {
    submitTrack() {
      // POST request using axios with error handling
      const newTrack = { trackUrl: this.trackUrl };
      console.log("posting track", newTrack);
      axios
        .post("http://localhost:4000/addtrack", newTrack)
        .then((response) => console.log(response.data))
        // .then((response) => (this.newTrack = response.data.id))
        .catch((error) => {
          this.errorMessage = error.message;
          console.error("There was an error!", error);
        });
    },
    keydown(event) {
      if (event.key === "Enter") {
        console.log("SUBMIT THROUGH KEYDOWN");
        this.submitTrack();
        this.playMusic();
      } else if (event.key === "Escape") {
        this.trackUrl = "";
        console.log("CLEARED INPUT");
      }
    },
    click() {
      // console.log();
      console.log("submit");
    },
    async playMusic() {
      console.log("play");
      let track = await axios.get("http://localhost:4000/");
      console.log(track);
    },
  },
};
</script>
