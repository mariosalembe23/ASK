<template>
  <aside
    class="fixed z-40 w-full p-5 h-screen top-0 left-0 bg-opacity-90 flex items-center justify-center right-0 bg-zinc-800"
  >
    <div
      class="max-w-xl card_message_lose shadow-lg w-full bg-zinc-700 p-5 rounded"
    >
      <header
        class="border-b border-zinc-600 pb-4 flex items-center justify-between"
      >
        <h2 class="flex items-center font-medium text-white">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-5 h-5 me-2 stroke-zinc-200"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M14.25 6.087c0-.355.186-.676.401-.959.221-.29.349-.634.349-1.003 0-1.036-1.007-1.875-2.25-1.875s-2.25.84-2.25 1.875c0 .369.128.713.349 1.003.215.283.401.604.401.959v0a.64.64 0 0 1-.657.643 48.39 48.39 0 0 1-4.163-.3c.186 1.613.293 3.25.315 4.907a.656.656 0 0 1-.658.663v0c-.355 0-.676-.186-.959-.401a1.647 1.647 0 0 0-1.003-.349c-1.036 0-1.875 1.007-1.875 2.25s.84 2.25 1.875 2.25c.369 0 .713-.128 1.003-.349.283-.215.604-.401.959-.401v0c.31 0 .555.26.532.57a48.039 48.039 0 0 1-.642 5.056c1.518.19 3.058.309 4.616.354a.64.64 0 0 0 .657-.643v0c0-.355-.186-.676-.401-.959a1.647 1.647 0 0 1-.349-1.003c0-1.035 1.008-1.875 2.25-1.875 1.243 0 2.25.84 2.25 1.875 0 .369-.128.713-.349 1.003-.215.283-.4.604-.4.959v0c0 .333.277.599.61.58a48.1 48.1 0 0 0 5.427-.63 48.05 48.05 0 0 0 .582-4.717.532.532 0 0 0-.533-.57v0c-.355 0-.676.186-.959.401-.29.221-.634.349-1.003.349-1.035 0-1.875-1.007-1.875-2.25s.84-2.25 1.875-2.25c.37 0 .713.128 1.003.349.283.215.604.401.96.401v0a.656.656 0 0 0 .658-.663 48.422 48.422 0 0 0-.37-5.36c-1.886.342-3.81.574-5.766.689a.578.578 0 0 1-.61-.58v0Z"
            />
          </svg>
          Acabou-se
        </h2>

        <button class="text-white transition-all hover:text-zinc-400" title="Desistir">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M5.636 5.636a9 9 0 1 0 12.728 0M12 3v9"
            />
          </svg>
        </button>
      </header>
      <div
        class="retrato-tablet:p-5 retrato-tablet:text-base text-[15px] py-5 text-white retrato-tablet:text-start text-center"
      >
        <p>
          Você Perdeu, suas Tentativas Esgotaram e Ficou sem Dinheiro!Tente
          Novamente.
        </p>
      </div>

      <footer class="pt-3 retrato-tablet:text-end text-center">
        <button
          @click="RestartGame"
          class="text-[15px] font-medium rounded text-white bg-indigo-700 transition-all hover:ring-4 hover:ring-indigo-600 px-4 py-2.5"
        >
          Recomeçar
        </button>
      </footer>
    </div>
  </aside>
</template>

<script>
export default {
  props: {
    restartGame: Function,
  },

  methods: {
    RestartGame() {
      this.restartGame();
    },
  },
};
</script>

<style scoped>
.card_message_lose {
  transform: scale(0.5);
  opacity: 0.2;
  animation: animationMessage 0.3s ease-in-out forwards;
}
@keyframes animationMessage {
  from {
    opacity: 0.2;
    transform: scale(0.5);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
</style>
