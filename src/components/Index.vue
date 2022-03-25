<script setup></script>

<template>
  <div
    class="
      mx-16
      lg:ml-[-20%] lg:mr-[15%] lg:px-[25vw] lg:px-[33]
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
        px-4
        py-4
        border-2 border-gray-700
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
        <input
          style="text-align: center"
          type="text"
          placeholder="YouTube or SoundCloud link here"
          class="h-12 mt-3 rounded-lg text-slate-600 w-full"
          name="URL"
        />

        <button
          class="
            flex
            align-self-end
            bg-orange-600
            text-white
            hover:bg-orange-500
            px-5
            text-lg text-align-center
            font-semibold
            rounded-lg
            py-2
            my-5
          "
        >
          Add Track
        </button>
      </div>
    </div>
  </div>
</template>
