<script>
import { AtomSpinner } from "epic-spinners";
import axios from "axios";
import LoseInfo from "./LoseInfo.vue";
import Navbar from "./Navbar.vue";
import Congrats from "./Congrats.vue";
import Settings from "./Settings.vue";
import Guia from './Guia.vue'

export default {
  data() {
    return {
      pointsInMoney: 100,
      buttonSelected: null,
      answerQuestion: "",
      questionsArray: [],
      questionsAlreadySelected: [],
      RecenteOptions: [],
      RecenteQuestion: "",
      CorrectAnswer: "",
      controllerChangeQuestion: 0,
      buttonDisabled: false,
      progressController: 1,
      playLose: false,
      loading: true,
      questionsFinished: false,
      wrongQuestions: 0,
      correct: 0,
      AbuttonSelected: true,
    };
  },

  components: {
    Navbar,
    LoseInfo,
    AtomSpinner,
    Congrats,
    Settings,
    Guia
  },

  mounted() {
    this.GetAllQuestions();
  },

  watch: {
    pointsInMoney(newPoints, oldPoints) {
      if (newPoints === 0 && oldPoints !== 0) {
        this.playLose = true;
      }
    },
  },

  methods: {
    selectButtonOption(buttonNumber, event) {
      this.buttonSelected = buttonNumber;
      this.answerQuestion = event.target.innerText;
      this.AbuttonSelected = false;
    },

    async GetAllQuestions() {
      try {
        const { data } = await axios.get(
          "https://gist.githubusercontent.com/morphosisUp/1e93810b5af5ea978b54966c44193cbd/raw/c3d59dbc01770c6ecc3e55268fc70f4357f9a557/questions"
        );

        this.questionsArray = await data.questions;

        this.RenderRandomQuestion();
      } catch (error) {
        console.error(`Ocorreu um erro ao Filtrar Questões: ${error}`);
      } finally {
        this.loading = false;
      }
    },
    VerifyAnswer() {
      const buttonSelectedChoose = document.querySelector(".buttonSelected");
      const AllButtonOption = document.querySelectorAll(".button_option");
      if (this.answerQuestion !== this.CorrectAnswer) {
        // RESPOSTA ERRADA
        this.wrongQuestions += 1;
        this.progressController += 1;
        buttonSelectedChoose.classList.add("incorrect_class");

        AllButtonOption.forEach((button) => {
          if (button.innerHTML === this.CorrectAnswer) {
            button.classList.add("correct_class");
          }
        });

        this.pointsInMoney -= 100;
        if (this.pointsInMoney <= 0) {
          this.playLose = true;
          return;
        }

        setTimeout(() => {
          this.RenderRandomQuestion();
        }, 1000);

        return;
      }
      this.progressController += 1;
      this.buttonDisabled = false;
      this.pointsInMoney += 150;
      this.correct += 1;

      if (buttonSelectedChoose.innerHTML === this.CorrectAnswer) {
        // IT'S CORRETC
        buttonSelectedChoose.classList.add("correct_class");
        setTimeout(() => {
          this.RenderRandomQuestion();
        }, 1000);
      }
    },
    RenderRandomQuestion() {
      const AllButtonOption = document.querySelectorAll(".button_option");

      AllButtonOption.forEach((button) => {
        button.classList.remove("correct_class");
      });
      this.AbuttonSelected = true;
      this.buttonSelected = null;
      this.controllerChangeQuestion = 0;
      const totalQuestions = this.questionsArray.length;

      if (this.questionsAlreadySelected.length >= totalQuestions) {
        this.questionsFinished = true;
        return;
      }

      let AleatoryIndex;

      do {
        AleatoryIndex = Math.floor(Math.random() * totalQuestions);
      } while (this.questionsAlreadySelected.includes(AleatoryIndex));

      this.questionsAlreadySelected.push(AleatoryIndex);

      console.table(this.questionsAlreadySelected);

      this.RecenteQuestion = this.questionsArray[AleatoryIndex].question;
      this.RecenteOptions = this.questionsArray[AleatoryIndex].options;
      this.CorrectAnswer = this.questionsArray[AleatoryIndex].answer;
    },
    RestartGameMain() {
      this.questionsFinished = false;
      this.wrongQuestions = 0;
      this.pointsInMoney = 100;
      this.playLose = false;
      this.progressController = 1;
      this.questionsAlreadySelected = [];
      this.RenderRandomQuestion();
    },

    ChangeQuestion() {
      this.buttonSelected = null;

      this.controllerChangeQuestion += 1;
      if (this.controllerChangeQuestion === 2) {
        this.buttonDisabled = true;
      } else {
        this.buttonDisabled = false;
      }
      const totalQuestions = this.questionsArray.length;
      const AleatoryIndex = Math.floor(Math.random() * totalQuestions);

      this.RecenteQuestion = this.questionsArray[AleatoryIndex].question;
      this.RecenteOptions = this.questionsArray[AleatoryIndex].options;
      this.CorrectAnswer = this.questionsArray[AleatoryIndex].answer;
    },
  },
};
</script>

<template>
  <main
    class="overflow-y-auto relative w-full retrato-tablet:h-screen flex retrato-tablet:m-0 mt-6 items-center justify-center"
  >
    <aside
      v-show="loading"
      class="absolute z-30 flex items-center justify-center top-0 left-0 right-0 w-full h-screen bg-[#242424]"
    >
      <atom-spinner :animation-duration="1000" :size="60" :color="'#4f46e5'" />
    </aside>
    <header>
      <div
        v-show="!playLose"
        class="fixed retrato-tablet:flex hidden justify-center ring-4 ring-indigo-600 my-5 ring-opacity-15 shadow-lg border border-indigo-700 items-center gap-2 right-5 top-2 bg-indigo-700 text-center rounded text-white px-6 py-2"
      >
        <h5 class="font-semibold">{{ pointsInMoney }}</h5>
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
      <header class="text-center mb-3">
        <div
          class="numeber_question m-auto bg-white ring-4 ring-white ring-opacity-40 w-10 h-10 rounded-full flex items-center justify-center"
        >
          <p class="font-bold text-xl text-[#242424]">
            {{ progressController }}
          </p>
        </div>

        <h1
          class="question pt-8 retrato-tablet:py-4 text-xl font-normal text-white"
        >
          {{ RecenteQuestion }}
        </h1>
        <div
          v-show="!playLose"
          class="retrato-tablet:hidden w-40 m-auto flex justify-center ring-4 ring-indigo-600 my-5 ring-opacity-15 shadow-lg border border-indigo-700 items-center gap-2 bg-indigo-700 text-center rounded text-white px-6 py-2"
        >
          <h5 class="font-semibold">{{ pointsInMoney }}</h5>
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
        <hr
          class="h-1 retrato-tablet:inline-flex hidden mb-4 rounded bg-zinc-600 border-none w-12 m-auto"
        />
      </header>

      <div class="container_options_ask retrato-tablet:w-4/5 m-auto">
        <div
          class="w-full grid retrato-tablet:grid-cols-2 grid-cols-2 smaller:grid-cols-1 gap-4"
        >
          <button
            v-for="(option, index) in RecenteOptions"
            :key="index"
            @click="selectButtonOption(index + 1, $event)"
            :class="{ buttonSelected: buttonSelected === index + 1 }"
            class="py-4 transition-all button_option p-2 hover:ring-[#666464] focus:ring-white focus:ring-opacity-10 hover:ring-opacity-25 hover:border-white rounded bg-[#242424] border border-zinc-700 ring-4 ring-[#444343] ring-opacity-15 shadow-lg text-white font-medium"
          >
            {{ option }}
          </button>
        </div>
        <div class="grid retrato-tablet:grid-cols-6 grid-cols-1 gap-3 mt-5">
          <button
            @click="VerifyAnswer"
            :disabled="AbuttonSelected"
            class="retrato-tablet:col-span-4 disabled:opacity-40 disabled:ring-0 py-3 bg-indigo-600 text-white rounded font-medium transition-all hover:ring-4 hover:ring-indigo-700 shadow-lg ring-opacity-15"
          >
            Responder
          </button>
          <button
            :disabled="buttonDisabled"
            @click="ChangeQuestion"
            class="retrato-tablet:col-span-2 disabled:opacity-25 py-3 disabled:ring-0 text-center font-medium rounded bg-zinc-800 shadow-lg transition-all hover:ring-4 hover:ring-zinc-800 ring-opacity-45 text-white"
          >
            Pular
          </button>
        </div>
      </div>
      <!-- <Navbar :pointsMoney="pointsInMoney" /> -->
      <LoseInfo
        v-show="playLose"
        :restartGame="RestartGameMain"
        :controllerLose="playLose"
      />
      <Congrats
        v-show="questionsFinished"
        :totalMoney="pointsInMoney"
        :numberWrongQuestions="wrongQuestions"
        :numberCorrectQuestions="correct"
        :functionRestartGame="RestartGameMain"
      />
     <!-- <Guia /> -->
    </div>
  </main>
</template>

<style scoped>
.buttonSelected {
  background-color: #fff !important;
  color: #242424 !important;
}
.correct_class {
  background-color: #4f46e5 !important;
  color: #fff !important;
}
.incorrect_class {
  background-color: rgb(228, 77, 51) !important;
  color: #fff !important;
}
</style>
