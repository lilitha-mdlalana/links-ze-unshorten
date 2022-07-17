<script setup lang="ts">
import { ref } from "vue";
import axios from "axios";

const link = ref("");

const submitLink = async () => {
  const options = {
    method: "GET",
    url: "https://free-url-un-shortener.p.rapidapi.com/url",
    params: { url: "https://bit.ly/19BiSHW" },
    headers: {
      "X-RapidAPI-Key": "62740a5305mshd310b6ba1ca7ebap1bc511jsndc27a95ddc56",
      "X-RapidAPI-Host": "free-url-un-shortener.p.rapidapi.com",
    },
  };

  axios
    .request(options)
    .then(function (response) {
      console.log(response.data);
    })
    .catch(function (error) {
      console.error(error);
    });
};
</script>

<template>
  <main class="h-screen bg-brand-primary flex items-center antialiased">
    <div class="w-1/2 pl-20">
      <p class="text-slate-200">URL unShortener</p>
      <h1 class="text-white text-4xl font-bold mt-2">
        Here you have full control over your links.
      </h1>
      <p class="text-slate-200 text-lg mt-2">
        Free URL Un-Shortener is a free service to Un-Shorten the URLs created
        by URL shortening services. This website can be used to un-shorten URLs created by
        different services like goo.gl (Google), fb.me (Facebook), t.co
        (Twitter), bit.ly, TinyURL, ow.ly among others.
      </p>
      <div id="cta">
        <button
          class="mt-4 px-5 py-3 rounded-xl bg-green-600 text-white hover:bg-white hover:text-brand-primary w-60 antialiased"
        >
          SIGN UP
        </button>
        <button
          class="mt-4 ml-3 px-5 py-3 rounded-xl bg-white/20 text-brand-primary/90 hover:bg-white w-60"
        >
          Pricing
        </button>
      </div>
    </div>
    <div class="w-1/2">
      <img
        class="mx-auto w-11/12"
        src="../assets/phone_mockup.png"
        alt="Link Shortener Mockup"
      />
    </div>
  </main>
  <section
    class="bg-brand-primary w-screen h-28 flex justify-center items-center"
  >
    <div id="input">
      <form @submit.prevent>
        <input
          type="text"
          class="py-4 rounded-tl-xl rounded-bl-xl focus:outline-none text-center w-[52rem]"
          placeholder="Paste shortened url and unshorten it"
          v-model="link"
        />
        <button
          @click="submitLink"
          type="submit"
          class="bg-green-600 py-4 px-6 text-white rounded-tr-xl rounded-br-xl"
        >
        Unshorten
        </button>
      </form>
    </div>
  </section>
</template>
