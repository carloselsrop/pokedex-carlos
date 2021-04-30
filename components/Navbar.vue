<template>
  <div class="flex justify-between py-4 px-8 items-center">
    <!-- Nav buttons -->
    <div class="flex space-x-14 w-1/3 sm:hidden lg:flex items-center">
      <NuxtLink to="/pokedex">
        <button class="flex items-center focus:outline-none">
          <img class="w-8" src="https://image.flaticon.com/icons/png/512/188/188940.png" alt="">
          <div class="font-semibold">
            Pokedex
          </div>
        </button>
      </NuxtLink>
      <NuxtLink to="/trainers">
        <button class="flex items-center focus:outline-none">
          <img class="w-10" src="https://images.wikidexcdn.net/mwuploads/esssbwiki/thumb/7/72/latest/20180614213310/Entrenador_Pok%C3%A9mon_%C3%ADcono_SSBU.png/180px-Entrenador_Pok%C3%A9mon_%C3%ADcono_SSBU.png" alt="">
          <div class="font-semibold">
            Entrenadores
          </div>
        </button>
      </NuxtLink>
      <NuxtLink to="/docu">
        <button class="flex items-center focus:outline-none">
          <img class="w-8" src="https://img.icons8.com/plasticine/452/journal.png" alt="">
          <div class="font-semibold">
            Documentacion
          </div>
        </button>
      </NuxtLink>
    </div>
    <!-- Pokemon logo -->
    <div class="w-1/3">
      <NuxtLink to="/">
        <button class="focus:outline-none">
          <img class="w-28" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/1280px-International_Pok%C3%A9mon_logo.svg.png" alt="">
        </button>
      </NuxtLink>
    </div>
    <!-- Account -->
    <div>
      <button class="focus:outline-none mr-4 relative" @click="isOpen = !isOpen">
        <img class="w-10" src="https://pngimg.com/uploads/pokeball/pokeball_PNG24.png" alt="">
      </button>
      <!-- Account options - Modal -->
      <div v-if="isOpen" class="absolute rounded ring-4 py-2 right-14 top-16">
        <div class="flex items-center">
          <div class="font-bold px-2">
            {{ trainer }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    isOpen: false,
    username: 'carlos'
  }),
  computed: {
    trainer () {
      return 'Bienvenido' + ' ' + 'entrenador' + ' ' + this.username
    }
  }
}
</script>
