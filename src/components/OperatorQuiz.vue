<template>
    <div>
        <h1 v-if="isQuizStarted">{{OperandLeft}} {{operator}} {{OperandRight}}</h1>
        <br>
        <div class="answers">
            <button type="button" @click="selectAnswer(answer)" v-for="(answer, index) in answers" :key="index">{{answer}}</button>
        </div>
        <button type="button" v-if="!isQuizStarted" v-on:click="startQuiz">Start</button>
        <button type="button" v-on:click="$emit('goBack')">Back</button>
    </div>
</template>
<script>
export default {
  props:['operator'],
  data() {
    return {
        OperandLeft : null,
        OperandRight : null,
        isQuizStarted : false,
        expectedAnswer : null,
        answers: []
    }
  },
  methods : {
    selectAnswer(selectedAnswer)
    {
        if(selectedAnswer !== this.expectedAnswer)
        {
            alert('WRONG ANSWER');
        }
        this.startQuiz();
    },
    shuffleArray(array) {
        for (var i = array.length - 1; i > 0; i--) {
            var j = Math.floor(Math.random() * (i + 1));
            var temp = array[i];
            array[i] = array[j];
            array[j] = temp;
        }
    },
    startQuiz()
    {
        this.isQuizStarted = true;
        this.OperandLeft = parseInt(Math.random() * 13) + 1;
        this.OperandRight = parseInt(Math.random() * 13) + 2;
        const methods = {
            '+': (a, b) => a + b,
            '-': (a, b) => a - b,
            '*': (a, b) => a * b,
            '/': (a, b) => a / b,
        };
        this.answers = [];
        var methodToUse = methods[this.operator];
        this.answers.push(methodToUse(this.OperandLeft + 1,this.OperandRight - 2));
        this.answers.push(methodToUse(this.OperandLeft + 1,this.OperandRight));
        this.answers.push(methodToUse(this.OperandLeft,this.OperandRight));
        this.answers.push(methodToUse(this.OperandLeft,this.OperandRight + 2));
        this.answers.push(methodToUse(this.OperandLeft,this.OperandRight - 1));
        this.shuffleArray(this.answers);
        this.expectedAnswer = methodToUse(this.OperandLeft,this.OperandRight);
    }
  }

}
</script>