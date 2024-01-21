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
            class="w-6 h-6 stroke-zinc-400 me-2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M15.182 16.318A4.486 4.486 0 0 0 12.016 15a4.486 4.486 0 0 0-3.198 1.318M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0ZM9.75 9.75c0 .414-.168.75-.375.75S9 10.164 9 9.75 9.168 9 9.375 9s.375.336.375.75Zm-.375 0h.008v.015h-.008V9.75Zm5.625 0c0 .414-.168.75-.375.75s-.375-.336-.375-.75.168-.75.375-.75.375.336.375.75Zm-.375 0h.008v.015h-.008V9.75Z"
            />
          </svg>

          Acabou-se
        </h2>

        <button
          class="text-white transition-all hover:text-zinc-400"
          title="Desistir"
        >
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
