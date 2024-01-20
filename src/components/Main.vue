<template>
  <main
    class="overflow-y-auto relative w-full retrato-tablet:h-screen flex retrato-tablet:m-0 mt-6 items-center justify-center"
  >
    <header>
      <div
        class="fixed retrato-tablet:flex hidden justify-center ring-4 ring-[#444343] ring-opacity-15 shadow-lg border border-zinc-700 items-center gap-2 top-5 bg-[#242424] text-center rounded text-white right-5 px-6 py-2"
      >
        <h5 class="font-semibold">100</h5>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          fill="currentColor"
          class="w-6 h-6"
        >
          <path
            fill-rule="evenodd"
            d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25Zm-1.902 7.098a3.75 3.75 0 0 1 3.903-.884.75.75 0 1 0 .498-1.415A5.25 5.25 0 0 0 8.005 9.75H7.5a.75.75 0 0 0 0 1.5h.054a5.281 5.281 0 0 0 0 1.5H7.5a.75.75 0 0 0 0 1.5h.505a5.25 5.25 0 0 0 6.494 2.701.75.75 0 1 0-.498-1.415 3.75 3.75 0 0 1-4.252-1.286h3.001a.75.75 0 0 0 0-1.5H9.075a3.77 3.77 0 0 1 0-1.5h3.675a.75.75 0 0 0 0-1.5h-3c.105-.14.221-.274.348-.402Z"
            clip-rule="evenodd"
          />
        </svg>
      </div>
    </header>

    <div class="container_question max-w-3xl w-full p-5">
      <header class="text-center">
        <div
          class="numeber_question m-auto bg-white ring-4 ring-white ring-opacity-40 w-10 h-10 rounded-full flex items-center justify-center"
        >
          <p class="font-bold text-xl text-[#242424]">1</p>
        </div>

        <h1 class="question pt-8 py-5 text-xl font-normal text-white">
          Quantos Anos de Existência tem a China?
        </h1>
      </header>

      <div class="container_options_ask retrato-tablet:w-4/5 m-auto">
        <!-- TIME TO ANSWER A QUESTION -->
        <div
          class="controllerTimeResponse w-full rounded bg-zinc-700 overflow-hidden shadow-lg mb-5"
        >
          <div class="progress w-1/2 rounded-full h-full py-1 bg-white"></div>
        </div>

        <div
          class="w-full grid retrato-tablet:grid-cols-2 grid-cols-2 smaller:grid-cols-1 gap-4"
        >
          <button
            class="py-4 transition-all hover:ring-[#666464] hover:ring-opacity-25 hover:border-white rounded bg-[#242424] border border-zinc-700 ring-4 ring-[#444343] ring-opacity-15 shadow-lg text-white font-medium text-xl"
          >
            120</button
          ><button
            class="py-4 transition-all hover:ring-[#666464] hover:ring-opacity-25 hover:border-white rounded bg-[#242424] border border-zinc-700 ring-4 ring-[#444343] ring-opacity-15 shadow-lg text-white font-medium text-xl"
          >
            90</button
          ><button
            class="py-4 transition-all hover:ring-[#666464] hover:ring-opacity-25 hover:border-white rounded bg-[#242424] border border-zinc-700 ring-4 ring-[#444343] ring-opacity-15 shadow-lg text-white font-medium text-xl"
          >
            244</button
          ><button
            class="py-4 transition-all hover:ring-[#666464] hover:ring-opacity-25 hover:border-white rounded bg-[#242424] border border-zinc-700 ring-4 ring-[#444343] ring-opacity-15 shadow-lg text-white font-medium text-xl"
          >
            111
          </button>
        </div>
        <div class="grid retrato-tablet:grid-cols-6 grid-cols-1 gap-3 mt-5">
          <button
            class="retrato-tablet:col-span-4 py-3 bg-indigo-600 text-white rounded font-medium transition-all hover:ring-4 hover:ring-indigo-700 shadow-lg ring-opacity-15"
          >
            Responder
          </button>
          <button
            class="retrato-tablet:col-span-2 py-3 text-center font-medium rounded bg-zinc-800 shadow-lg transition-all hover:ring-4 hover:ring-zinc-800 ring-opacity-45 text-white"
          >
            Pular
          </button>
        </div>
      </div>
    </div>
  </main>
</template>

<script></script>
