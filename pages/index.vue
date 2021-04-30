<template>
  <div>
    <Navbar />
    <div class="w-full back bg-cover bg-center  flex flex-col items-center justify-center">
      <div class="py-4">
        <img class="w-32" src="https://i.pinimg.com/originals/f8/7f/f0/f87ff0ddf2874b20d8c3c37b10681a35.png" alt="">
      </div>
      <!-- Search Box -->
      <div class="bg-white sm:w-10/12 md:w-6/12 xl:w-4/12 px-8 py-2 rounded-lg relative">
        <div class="text-sm font-bold py-1">
          Busca tu pokemon favorito
        </div>
        <!-- Magnifiying glass button -->
        <div class="absolute right-12 top-12">
          <button class="focus:outline-none" @click="addRecentSearch">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
              <path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" />
            </svg>
          </button>
        </div>
        <!-- Input -->
        <audio ref="pika" src="/pika.mp3" />
        <input v-model="searchPokemon" class="bg-gray-200 w-full py-2 rounded px-2 focus:outline-none border-2 border-white focus:border-yellow-400 duration-300" type="text" placeholder="Alakazam..." @click="playPika()">
        <div class="flex mt-2">
          <button :class="{'bg-gray-300' : isClicked, 'bg-white' : isClicked === false}" class="w-1/2 py-2 focus:outline-none text-center text-sm rounded-md" @click="searchOptions = true, isClicked = true">
            Busquedas recientes
          </button>
          <button :class="{'bg-gray-300' : isClicked === false, 'bg-white' : isClicked === true}" class="w-1/2 py-2 focus:outline-none text-center text-sm rounded-md" @click="searchOptions = false, isClicked = false">
            Pokemones favoritos
          </button>
        </div>
        <!-- Search features -->
        <div class="w-full flex">
          <!-- Recently searchs -->
          <div v-show="searchOptions" class="w-full text-center">
            <ul class="py-4 space-y-2">
              <li v-for="(recent, index) in recentlySearch" :key="recent" class="flex justify-center">
                <button class="text-gray-300 mr-2 focus:outline-none" @click="spliceOnRecent(index)">
                  x
                </button>
                {{ recent.recent }}
              </li>
            </ul>
            <div v-if="recentlySearch.length === 0" class="text-gray-400 text-sm text-center pb-4">
              No ha realizado una busqueda de ningun pokemon
            </div>
          </div>
          <!-- Favorites pokemons -->
          <div v-show="searchOptions === false" class="w-full text-center">
            <ul class="py-4 space-y-2">
              <li v-for="(favorites, index) in favoritesPokemons" :key="favorites" class="flex justify-center ">
                <button class="text-gray-300 mr-2 focus:outline-none" @click="spliceOnFavorites(index)">
                  x
                </button> {{ favorites.fav }}
              </li>
            </ul>
            <div v-if="favoritesPokemons.length === 0" class="flex justify-center text-gray-400 text-sm pb-4">
              Puedes agregar un pokemon en
              <svg xmlns="http://www.w3.org/2000/svg" class="px-1 h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z" />
              </svg>
              para ver sus actualizaciones.
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    searchPokemon: '',
    searchOptions: true,
    isClicked: true,
    recentlySearch: [
      { recent: 'Bulbasaur' },
      { recent: 'Ivysaur' },
      { recent: 'Charizard' },
      { recent: 'Mewtwo' },
      { recent: 'Arceus' }
    ],
    favoritesPokemons: [
      { fav: 'Charizard' },
      { fav: 'Arceus' }
    ]
  }),
  methods: {
    spliceOnRecent (index) {
      this.recentlySearch.splice(index, 1)
    },
    spliceOnFavorites (index) {
      this.favoritesPokemons.splice(index, 1)
    },
    addRecentSearch () {
      if (this.recentlySearch.length === 5) {
        this.recentlySearch.pop()
      }
      this.recentlySearch.unshift({ recent: this.searchPokemon })
    },
    playPika () {
      this.$refs.pika.play()
    }
  }
}
</script>

<style>
.back{
  height: 858px;
  background-image: url('https://i.pinimg.com/originals/52/69/0c/52690c8c4d930ba7ea669442b3a466ad.png');
}
</style>
