<template>
  <div
    class="center bg-white w-full h-auto p-1 pb-4 m-0 flex flex-col items-center"
  >
    <h3 class="m-0 mt-3">
      ٱلسَّلَامُ عَلَيْكُمْ وَرَحْمَةُ ٱللَّٰهِ وَبَرَكَاتُهُ
    </h3>
    <h1 class="text-3xl leading-snug my-2">Benvenuta Zannuba! 🌴</h1>
    <TipCard></TipCard>
    <div
      class="w-full h-auto p-2 pt-7 flex flex-row justify-around items-center"
    >
      <button
        @click="prev"
        class="p-1 px-2 rounded bg-green-700 text-white shadow-2xl"
      >
        Precedente
      </button>
      <button
        @click="saveNcopy"
        class="p-1 px-2 rounded bg-green-600 text-white shadow-2xl"
      >
        Salva & Copia
      </button>
      <button
        @click="next"
        class="p-1 px-2 rounded bg-green-700 text-white shadow-2xl"
      >
        Successivo
      </button>
    </div>
    <friend-list v-model:nomi="lettori" />
    <span>Made with ❤ by Ali for Zeineb</span>
  </div>
</template>

<script>
import FriendList from "./components/FriendList";
import TipCard from "./components/TipCard";
import { lettori } from "./assets/initData";

export default {
  name: "App",
  components: {
    FriendList,
    TipCard,
  },
  data() {
    return {
      lettori,
    };
  },
  mounted() {
    const storage = window.localStorage;
    if (storage.getItem("khatma")) {
      const data = storage.getItem("khatma");
      this.lettori = JSON.parse(data);
    }
  },
  methods: {
    next: function () {
      const last = this.lettori.pop();
      this.lettori.unshift(last);
    },
    prev: function () {
      const first = this.lettori.shift();
      this.lettori.push(first);
    },
    saveNcopy: function () {
      const storage = window.localStorage;
      const parsedData = JSON.stringify(this.lettori);
      storage.setItem("khatma", parsedData);
    },
  },
};
</script>

<style lang="postcss">
@import url("https://fonts.googleapis.com/css2?family=Comfortaa&family=Nunito&family=Reem+Kufi&display=swap");
#app {
  @apply font-sans antialiased text-center h-full w-full text-gray-800;
}

h1 {
  font-family: Comfortaa;
  font-weight: 700;
}
</style>
