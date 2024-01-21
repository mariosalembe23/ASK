<template>
  <aside
    class="fixed z-40 w-full p-5 h-screen top-0 left-0 bg-opacity-90 flex items-center justify-center right-0 bg-zinc-700"
  >
    <div
      class="fixed container_congrats overflow-y-auto bottom-0 right-0 left-0 rounded-t-3xl retrato-tablet:h-[30rem] h-full bg-zinc-800 p-5"
    >
      <header class="text-center border-zinc-700 py-3">
        <h3 class="text-xl font-medium text-white">Parabéns</h3>
        <hr class="m-auto h-1 border-none bg-zinc-600 rounded w-14 my-3" />
      </header>
      <div class="mt-2 max-w-3xl w-full mx-auto">
        <div class="w-full text-center">
          <a href="#" class="text-2xl font-bold text-zinc-500"
            >A<span class="text-white">S</span>K</a
          >
          
        </div>

        <div class="grid grid-cols-1 mt-6 gap-6">
          <div
            class="flex px-2 items-center border-b pb-4 border-zinc-700 justify-between"
          >
            <p class="flex items-center font-medium text-white">
              {{ totalMoney }}
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                fill="currentColor"
                class="w-6 h-6 ms-1"
              >
                <path
                  fill-rule="evenodd"
                  d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25Zm-1.902 7.098a3.75 3.75 0 0 1 3.903-.884.75.75 0 1 0 .498-1.415A5.25 5.25 0 0 0 8.005 9.75H7.5a.75.75 0 0 0 0 1.5h.054a5.281 5.281 0 0 0 0 1.5H7.5a.75.75 0 0 0 0 1.5h.505a5.25 5.25 0 0 0 6.494 2.701.75.75 0 1 0-.498-1.415 3.75 3.75 0 0 1-4.252-1.286h3.001a.75.75 0 0 0 0-1.5H9.075a3.77 3.77 0 0 1 0-1.5h3.675a.75.75 0 0 0 0-1.5h-3c.105-.14.221-.274.348-.402Z"
                  clip-rule="evenodd"
                />
              </svg>
            </p>

            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-5 h-5 stroke-green-500 stroke-2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="m4.5 12.75 6 6 9-13.5"
              />
            </svg>
          </div>
          <div
            class="flex px-2 items-center border-b pb-4 border-zinc-700 justify-between"
          >
            <p class="flex items-center font-medium text-white">
              + 15 Respostas Certas
            </p>

            <svg
              v-if="numberCorrectQuestions > 15"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-5 h-5 stroke-green-500 stroke-2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="m4.5 12.75 6 6 9-13.5"
              />
            </svg>

            <svg
              v-else
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="w-6 h-6 fill-red-400"
            >
              <path
                fill-rule="evenodd"
                d="M5.47 5.47a.75.75 0 0 1 1.06 0L12 10.94l5.47-5.47a.75.75 0 1 1 1.06 1.06L13.06 12l5.47 5.47a.75.75 0 1 1-1.06 1.06L12 13.06l-5.47 5.47a.75.75 0 0 1-1.06-1.06L10.94 12 5.47 6.53a.75.75 0 0 1 0-1.06Z"
                clip-rule="evenodd"
              />
            </svg>
          </div>
          <div
            class="flex px-2 items-center border-b pb-4 border-zinc-700 justify-between"
          >
            <p class="flex items-center font-medium text-white">
              Respostas Erradas / Corretas
            </p>

            <div class="flex items-center gap-1">
              <p class="font-medium text-red-400">
                {{ numberWrongQuestions }}
              </p>
              <span class="text-zinc-200">/</span>
              <p class="text-green-500">{{ numberCorrectQuestions }}</p>
            </div>
          </div>
          <div
            class="flex retrato-tablet:flex-row flex-col items-center gap-2 justify-center"
          >
            <button
              @click="RestartGame"
              class="bg-indigo-700 px-6 retrato-tablet:w-32 w-full py-2 rounded text-white font-medium transition-all hover:ring-2 hover:ring-indigo-600"
            >
              Reiniciar
            </button>
            <button
              class="bg-zinc-700 px-6 py-2 retrato-tablet:w-32 w-full rounded text-white font-medium transition-all hover:ring-2 hover:ring-zinc-600"
            >
              Sair
            </button>
          </div>
        </div>
      </div>
    </div>
  </aside>
</template>

<script>
export default {
  props: {
    totalMoney: Number,
    numberWrongQuestions: Number,
    numberCorrectQuestions: Number,
    functionRestartGame: Function,
  },

  methods: {
    RestartGame() {
      this.functionRestartGame();
    },
  },
};
</script>

<style scoped>
.container_congrats {
  transform: translateY(100%);
  transition: transform 0.6s ease-in-out;
  animation: showCongratsCard 0.5s ease-in-out forwards;
}
@keyframes showCongratsCard {
  from {
    transform: translateY(100%);
  }
  to {
    transform: translateY(0%);
  }
}
</style>
