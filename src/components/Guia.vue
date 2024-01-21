<template>
  <aside
    class="fixed z-40 w-full retrato-tablet:p-5 h-screen top-0 left-0 bg-opacity-90 flex items-center justify-center right-0 bg-zinc-800"
  >
    <div
      class="max-w-3xl h-full cardGuide retrato-tablet:h-[30rem] flex flex-col justify-between shadow-lg m-auto w-full p-5 retrato-tablet:rounded rounded-none bg-zinc-700"
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
          Guia
        </h2>
      </header>
      <div class="mt-3 h-full overflow-y-auto w-full">
        <div class="intrudution p-3">
          <p
            class="text-white text-[15px] text-balance font-['Inter'] leading-7"
          >
            Este é um Jogo de Perguntas Sobre Curiosidades Sobre o Mundo e a
            medida que vai acertando as questões podes ganhar
            <span class="px-4 py-1 rounded bg-indigo-600 font-medium">150</span>
            Euros por cada Resposta Certa, mas a medida que vai errando as
            questões, perdes
            <span class="px-4 py-1 rounded bg-red-600 font-medium">100</span>
            Euros. São 60 Perguntas, Acerte o Máximo que Poder.
          </p>
        </div>
        <div class="px-3 py-2">
          <h6 class="text-white font-medium text-xl">Propriedades</h6>
          <ul class="mt-3 space-y-3">
            <li class="font-['Inter'] leading-7 text-[15px] text-white">
              <span
                class="font-medium mx-1 text-zinc-300 px-4 bg-indigo-700 rounded py-1"
              >
                Pular Questões
              </span>
              Podes Pular questões Difíceis para Responder Noutra Altura. Tens
              Duas Tentativas para Pular Questões em Cada Jogada!
            </li>
            <li class="font-['Inter'] leading-7 text-[15px] text-white">
              <span
                class="font-medium mx-1 text-zinc-300 px-4 bg-indigo-700 rounded py-1"
              >
                Contribuir
              </span>
              Caso Tenha uma Ideia de Melhoria do Projecto, poderá Sugerir Uma
              Ideia, Modificação ou Melhoria!
            </li>
            <li
              class="font-['Inter'] font-medium leading-7 text-[15px] text-white"
            >
              O Jogo Termina quando o seu Total de Dinheiro For 0.
            </li>
          </ul>
        </div>
      </div>
      <footer class="text-end">
        <button
        @click="CloseGuideCard"
          class="text-white px-6 py-2 rounded font-medium transition-all hover:ring-2 hover:ring-indigo-600 bg-indigo-600"
        >
          OK
        </button>
      </footer>
    </div>
  </aside>
</template>

<script>
export default {
  props: {
    closeGuideFunction: Function,
  },

  methods: {
    CloseGuideCard() {
      this.closeGuideFunction();
    },
  },
};
</script>

<style>
.cardGuide {
  transform: scale(0.5);
  opacity: 0.2;
  animation: showGuide 0.4s ease-in-out forwards;
}

@keyframes showGuide {
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
