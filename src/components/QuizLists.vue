<script>
    export default {
        props: {
            quizStarted: {
                type: Boolean,
                required: true,
            }
        }
    }
</script>

<template>
    <div class="container">
        <div class="quiz-card" @click="$emit('startQuizForMath')" v-show="!quizStarted">
            <h2>Math</h2>
            <hr>
            <img src="https://t3.ftcdn.net/jpg/01/03/66/62/360_F_103666209_tFeb6hdeIeaBzqhuG1fWc5R44OYd00nk.jpg" alt="">
        </div>
        <div class="quiz-card" @click="$emit('startQuizForBiology')" v-show="!quizStarted">
            <h2>Biology</h2>
            <hr>
            <img src="https://png.pngtree.com/png-vector/20191016/ourmid/pngtree-biology-micro-bacteria-vector-sign-thin-line-icon-png-image_1804114.jpg"
                alt="">
        </div>
        <div class="quiz-card" @click="$emit('startQuizForHistory')" v-show="!quizStarted">
            <h2>History</h2>
            <hr>
            <img src="https://us.123rf.com/450wm/gow27/gow271601/gow27160100152/51173724-stock-vector-history-education-subject-handwriting-doodle-icon-of-landmark-location-culture-sign-and-symbol-white.jpg?ver=6"
                alt="">
        </div>
    </div>
</template>

<style scoped>
    .container {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        margin: 15px;
    }

    .quiz-card {
        height: 270px;
        width: 300px;
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
        animation: quiz-card;
        animation-duration: 0.8s;
        animation-fill-mode: forwards;
    }

    .quiz-card:hover {
        transform: scale(1.1);
    }

    img {
        height: 200px;
        width: auto;
        display: block;
        margin-top: 10px;
        margin-left: auto;
        margin-right: auto;
        border-radius: 15px;
    }

    @keyframes quiz-card {
        0% {
            transform: scale(0);
            opacity: 0;
        }

        100% {
            transform: scale(1);
            opacity: 1;
        }
    }
</style>