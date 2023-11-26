<script>
    export default {
        props: {
            quizFinished: {
                type: Boolean,
                required: true,
            },
            yourScore: {
                type: Number,
                required: true,
            },
            mathQuiz: {
              type: Boolean,
              required: true,
            },
            biologyQuiz: {
              type: Boolean,
              required: true,
            },
            historyQuiz: {
              type: Boolean,
              required: true,
            }, 
        },
    }
</script>

<template>
        <div v-if="quizFinished" class="quiz-finished">
          <div class="image-section">
            <img src="https://thumbs.gfycat.com/PeacefulNecessaryGrasshopper-max-1mb.gif" alt="GIF"
              v-show="yourScore > 30">
             <img src="https://media.tenor.com/xx7GpzF7r4wAAAAM/just-ok-nod.gif" alt="GIF" v-show="yourScore === 30"> 
            <img src="https://media.tenor.com/P8OYV56HSRAAAAAM/cry-sad.gif" alt="GIF" v-show="yourScore <= 20">
          </div>
          <div class="score-section">
            <p>Score: {{ yourScore }}</p>
            <hr>
            <p v-if="yourScore >= 40" class="green"> You got perfect score for this quiz</p>
            <p v-if="yourScore === 30" class="yellow">Your score is almost perfect</p>
            <p v-if="yourScore <= 20" class="red">Your score is low as fuck, go fuckin study again</p>
          
            <button @click="$emit('restartQuizForMath')" v-show="mathQuiz">Restart Math Quiz</button>
            <button @click="$emit('restartQuizForHistory')" v-show="historyQuiz">Restart History Quiz</button>
            <button @click="$emit('restartQuizForBiology')" v-show="biologyQuiz">Restart Biology Quiz</button>
            <button @click="$emit('returnHome')">Return Home</button>
          </div>
          </div>
</template>

<style scoped>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    .quiz-finished {
    display: flex;
    /* flex-direction: column; */
    justify-content: space-around;
    flex-wrap: wrap;
    /* text-align: center; */
  }

  .quiz-finished img {
    height: 250px;
    width: 300px;
    margin: auto;
    border-radius: 15px;
  }
  .green {
    color: #2ecc71;
  }
  .yellow {
    color: #f1c40f;
  }
  .red {
    color: #e84118;
  }
  button {
    font-family: 'Poppins';
    background-color: rgba(0, 0, 0, 0.75);
    color: white;
    width: 100%;
    border: none;
    padding: 7px;
    border-radius: 15px;
    cursor: pointer;
    margin-top: 10px;
    margin-bottom: 3px;
    animation-name: button-animation;
    animation-duration: 1s;
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