<script>
  import QuizLists from '../components/QuizLists.vue';
  import QuizFinished from '../components/QuizFinished.vue';

  export default {
    components: {
      QuizLists,
      QuizFinished,
    },
    data() {
      return {
        quizStarted: false,
        mathQuiz: false,
        biologyQuiz: false,
        historyQuiz: false,
        hideLine: false,
        currentQuestionIndex: 0,
        selectedOption: '',
        answered: false,
        yourScore: 0,
        quizFinished: false,
        mathQuestions: [{
            question: '1 + 1 = ...',
            options: ['2', '3', '4'],
            answer: '2',
            number: 1,
          },
          {
            question: '30 x 2 = ...',
            options: ['23', '60', '32'],
            answer: '60',
            number: 2,
          },
          {
            question: '50 + 30 = ...',
            options: ['25', '80', '40'],
            answer: '80',
            number: 3,
          },
          {
            question: '50 - 25 = ...',
            options: ['26', '32', '25'],
            answer: '25',
            number: 4,
          },
          {
            question: '100 : 25 = ...',
            options: ['3', '8', '4'],
            answer: '4',
            number: 5,
          }
        ],
        questions: [{
            question: 'Apa itu simbiosis mutualisme?',
            options: ['Hubungan yang saling menguntungkan', 'Hubungan yang hanya menguntungkan satu pihak',
              'Hubungan yang tidak menguntungkan kedua pihak'
            ],
            answer: 'Hubungan yang saling menguntungkan',
            number: 1,
          },
          {
            question: 'Apa itu klorofil?',
            options: ['Zat hijau pada daun', 'Zat biru pada daun', 'Zat lembut pada daun'],
            answer: 'Zat hijau pada daun',
            number: 2,
          },
          {
            question: 'Siapa penemu teori evolusi?',
            options: ['Charles Darwin', 'Albert Einstein', 'Nikola Tesla'],
            answer: 'Charles Darwin',
            number: 3,
          },
          {
            question: 'Hewan pemakan daging disebut dengan?',
            options: ['Karnivora', 'Omnivora', 'Herbivora'],
            answer: 'Karnivora',
            number: 4,
          },
          {
            question: 'Siapa penghasil oksigen terbanyak di bumi?',
            options: ['Pohon', 'Fitoplankton', 'Ikan'],
            answer: 'Fitoplankton',
            number: 5,
          }
        ],
        historyQuestions: [{
            question: 'Siapa yang menyuruh Christopher Columbus untuk menjelajahi dunia?',
            options: ['Raja Spanyol Ferdinand', 'Napoleon Bonaparte', 'Benjamin Franklin'],
            answer: 'Raja Spanyol Ferdinand',
            number: 1,
          },
          {
            question: 'Kapan perang dingin terjadi?',
            options: ['1920-1930', '1947-1948', '1942-1943'],
            answer: '1947-1948',
            number: 2,
          },
          {
            question: 'Siapa penemu lampu listrik?',
            options: ['Thomas Edison', 'Albert Einstein', 'Isaac Newton'],
            answer: 'Thomas Edison',
            number: 3,
          },
          {
            question: 'Kapan internet menjadi populer?',
            options: ['1991', '1992', '1993'],
            answer: '1993',
            number: 4,
          },
          {
            question: 'Siapakah pemilik lukisan terkenal Starry Night?',
            options: ['Vincent van Gogh', 'Pablo Picasso', 'Leonardo Davinci'],
            answer: 'Vincent van Gogh',
            number: 5,
          }
        ]
      }
    },
    computed: {
      currentMathQuestion() {
        if (this.quizFinished) {
          return null;
        } else {
          return this.mathQuestions[this.currentQuestionIndex];
        }
      },
      currentQuestion() {
        if (this.quizFinished) {
          return null;
        } else {
          return this.questions[this.currentQuestionIndex];
        }
      },
      currentHistoryQuestion() {
        if (this.quizFinished) {
          return null;
        } else {
          return this.historyQuestions[this.currentQuestionIndex];
        }
      },

    },
    methods: {
      startQuizForMath() {
        this.quizStarted = true;
        this.mathQuiz = true;

        setTimeout(() => {
          this.hideLine = true;
        }, 2000);
      },
      startQuizForBiology() {
        this.quizStarted = true;
        this.biologyQuiz = true;

        setTimeout(() => {
          this.hideLine = true;
        }, 2000);
      },
      startQuizForHistory() {
        this.quizStarted = true;
        this.historyQuiz = true;

        setTimeout(() => {
          this.hideLine = true;
        }, 2000);
      },
      submitAnswer() {
        this.answered = true;
        if (this.selectedOption === this.currentQuestion?.answer || this.selectedOption === this.currentMathQuestion?.answer || this.selectedOption === this.currentHistoryQuestion?.answer) {
          this.score++;
          this.yourScore += 10;
        }
      },
      nextQuestion() {
        this.answered = false;
        this.selectedOption = '',
          this.currentQuestionIndex++;
        if (this.currentQuestionIndex === this.questions.length || this.currentQuestionIndex === this.mathQuestions
          .length || this.currentQuestionIndex === this.historyQuestions) {
          this.quizFinished = true;
        }
      },
      restartQuizForMath() {
        this.quizStarted = true;
        this.quizFinished = false;
        this.biologyQuiz = false;
        this.mathQuiz = true;
        this.historyQuiz = false;
        this.currentQuestionIndex = 0;
        this.selectedOption = '';
        this.answered = false;
        this.yourScore = 0;
      },
      restartQuizForBiology() {
        this.quizStarted = true;
        this.quizFinished = false;
        this.biologyQuiz = true;
        this.mathQuiz = false;
        this.historyQuiz = false;
        this.currentQuestionIndex = 0;
        this.selectedOption = '';
        this.answered = false;
        this.yourScore = 0;
      },
      restartQuizForHistory() {
        this.quizStarted = true;
        this.quizFinished = false;
        this.biologyQuiz = false;
        this.mathQuiz = false;
        this.historyQuiz = true;
        this.currentQuestionIndex = 0;
        this.selectedOption = '';
        this.answered = false;
        this.yourScore = 0;
      },
      returnHome() {
        this.quizStarted = false;
        this.quizFinished = false;
        this.mathQuiz = false;
        this.biologyQuiz = false;
        this.historyQuiz = false;
        this.currentQuestionIndex = 0;
        this.selectedOption = '';
        this.answered = false;
        this.yourScore = 0;
      },
    }
  }
</script>

<template>
  <main>
    <QuizLists :quizStarted="quizStarted" @startQuizForMath="startQuizForMath"
      @startQuizForBiology="startQuizForBiology" @startQuizForHistory="startQuizForHistory" />


    <div class="container">
      <div class="line-animation" :class="{ 'hidden': hideLine }" v-show="quizStarted"></div>

      <div class="question-card" v-show="mathQuiz === true && hideLine === true">
        <div class="header-title" v-if="!quizFinished">
          <h2>Math Quiz</h2>
          <h2>{{ currentMathQuestion.number }}/{{ mathQuestions.length }}</h2>
        </div>
        <hr v-if="!quizFinished">
        <div class="question-content">
          <h3 v-if="currentMathQuestion">{{ currentMathQuestion.question }}</h3>
          <ul v-if="!quizFinished">
            <li v-for="optionForMath in currentMathQuestion.options" :key="optionForMath">
              <label>
                <input type="radio" :value="optionForMath" v-model="selectedOption" :disabled="answered" />
                {{ optionForMath }}
              </label>
            </li>
          </ul>
          <button @click="submitAnswer" :disabled="!selectedOption || answered"
            v-show="!quizFinished && selectedOption">
            Submit Answer
          </button>
          <div v-if="answered && currentMathQuestion">
            <button @click="nextQuestion">Next Question</button>
          </div>
          <QuizFinished :quizFinished="quizFinished" :mathQuiz="mathQuiz" :biologyQuiz="biologyQuiz"
            :historyQuiz="historyQuiz" :yourScore="yourScore" @restartQuizForMath="restartQuizForMath"
            @returnHome="returnHome" />
        </div>
      </div>


      <div class="question-card" v-show="biologyQuiz === true && hideLine === true">
        <div class="header-title" v-if="!quizFinished">
          <h2>Biology Quiz</h2>
          <h2>{{ currentQuestion.number }}/{{ questions.length }}</h2>
        </div>
        <hr v-if="!quizFinished">
        <div class="question-content">
          <h3 v-if="currentQuestion">{{ currentQuestion.question }}</h3>
          <ul v-if="currentQuestion">
            <li v-for="option in currentQuestion.options" :key="option">
              <label>
                <input type="radio" :value="option" v-model="selectedOption" :disabled="answered" />
                {{ option }}
              </label>
            </li>
          </ul>
          <button @click="submitAnswer" :disabled="!selectedOption || answered"
            v-show="!quizFinished && selectedOption">
            Submit Answer
          </button>
          <div v-if="answered && currentQuestion">
            <button @click="nextQuestion">Next Question</button>
          </div>
          <QuizFinished :quizFinished="quizFinished" :mathQuiz="mathQuiz" :biologyQuiz="biologyQuiz"
            :historyQuiz="historyQuiz" :yourScore="yourScore" @restartQuizForBiology="restartQuizForBiology"
            @returnHome="returnHome" />
        </div>
      </div>


      <div class="question-card" v-show="historyQuiz === true && hideLine === true">
        <div class="header-title" v-if="!quizFinished">
          <h2>History Quiz</h2>
          <h2>{{ currentHistoryQuestion.number }}/{{ historyQuestions.length }}</h2>
        </div>
        <hr v-if="!quizFinished">
        <div class="question-content">
          <h3 v-if="currentHistoryQuestion">{{ currentHistoryQuestion.question }}</h3>
          <ul v-if="currentHistoryQuestion">
            <li v-for="optionForHistory in currentHistoryQuestion.options" :key="optionForHistory">
              <label>
                <input type="radio" :value="optionForHistory" v-model="selectedOption" :disabled="answered" />
                {{ optionForHistory }}
              </label>
            </li>
          </ul>
          <button @click="submitAnswer" :disabled="!selectedOption || answered"
            v-show="!quizFinished && selectedOption">
            Submit Answer
          </button>
          <div v-if="answered && currentHistoryQuestion">
            <button @click="nextQuestion">Next Question</button>
          </div>
          <QuizFinished :quizFinished="quizFinished" :mathQuiz="mathQuiz" :biologyQuiz="biologyQuiz"
            :historyQuiz="historyQuiz" :yourScore="yourScore" @restartQuizForHistory="restartQuizForHistory"
            @returnHome="returnHome" />
        </div>
      </div>



    </div>
  </main>
</template>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .container {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    margin: 15px;
  }

  .question-card {
    /* height: 400px; */
    width: 800px;
    padding: 10px;
    margin: 10px auto;
    cursor: pointer;
    background-color: #fff;
    border-radius: 15px;
    border: 2px solid #0984e3;
    transition: ease-in-out 0.7s;
    box-shadow: 10px 10px 0px 0px rgba(0, 0, 0, 0.75);
    -webkit-box-shadow: 10px 10px 0px 0px rgba(0, 0, 0, 0.75);
    -moz-box-shadow: 10px 10px 0px 0px rgba(0, 0, 0, 0.75);
    animation: question-card;
    animation-duration: 0.5s;
    animation-fill-mode: forwards;
  }

  .question-card .header-title {
    display: flex;
    justify-content: space-between;
  }

  .question-content {
    padding: 10px;
    margin-top: 10px;
    border-radius: 15px;
  }

  .question-content ul {
    list-style-type: none;
    margin-top: 10px;
    margin-bottom: 10px;
  }

  .question-content li {
    margin-bottom: 5px;
    background-color: #dddd;
    padding: 8px;
    border-radius: 15px;
  }

  .question-content button {
    font-family: 'Poppins';
    background-color: rgba(0, 0, 0, 0.75);
    color: white;
    width: 100%;
    border: none;
    padding: 7px;
    border-radius: 15px;
    cursor: pointer;
    margin-top: 5px;
    margin-bottom: 5px;
    animation-name: button-animation;
    animation-duration: 1s;
  }

  .line-animation {
    width: 0;
    height: 2px;
    background-color: black;
    animation-name: lineStretch;
    animation-duration: 1s;
    animation-fill-mode: forwards;
  }

  @keyframes question-card {
    0% {
      transform: scale(0);
      opacity: 0;
    }

    100% {
      transform: scale(1);
      opacity: 1;
    }
  }

  @keyframes lineStretch {
    0% {
      width: 0;
    }

    100% {
      width: 100%;
    }
  }

  .hidden {
    display: none;
  }

  @keyframes button-animation {
    0% {
      opacity: 0;
    }

    100% {
      opacity: 1;
    }
  }
</style>