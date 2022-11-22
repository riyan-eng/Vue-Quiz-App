<template>
    <div>
        <div v-if="isStarted">
            <h4>{{ operandLeft }} {{ operator }} {{ operandRight }}</h4>
            <button @click="onSelect(answer)" v-for="answer, index in answers" :key="index">
                {{answer}} 
            </button>
        </div>
        <div v-if="!isStarted">

            <button @click="onStart">Start</button>
        </div>
        <button @click="$emit('onBack')">Back</button>
    </div>
</template>

<script>
export default {
    name: 'OpeatorQuiz',
    props: {
        operator: String
    },
    data() {
        return {
            operandLeft: null,
            operandRight: null,
            isStarted : false,
            answers : [],
            expectedAnswer : null
        }
    },
    methods: {
        onStart() {
            this.isStarted = true
            this.operandLeft = parseInt(Math.random() * 13)
            this.operandRight = parseInt(Math.random() * 13)

            const methods = {
                '+': (a,b) => a+b,
                '-': (a,b) => a-b,
                '/': (a,b) => a/b,
                '*': (a,b) => a*b,
            }

            const methodUse = methods[this.operator]
            this.answers = []
            this.answers.push(methodUse(this.operandLeft, this.operandRight + 1))
            this.answers.push(methodUse(this.operandLeft + 1, this.operandRight))
            this.answers.push(methodUse(this.operandLeft + 1, this.operandRight + 1))
            this.answers.push(methodUse(this.operandLeft - 1, this.operandRight + 1))
            this.answers.push(methodUse(this.operandLeft, this.operandRight - 1))

            const expectedAnswer = methodUse(this.operandLeft, this.operandRight)
            this.answers[parseInt(Math.random * this.answers.length)] = expectedAnswer
            this.expectedAnswer = expectedAnswer
        },

        onSelect(answerSelected){
            if (answerSelected === this.expectedAnswer){
                this.onStart()
            } else{
                alert("Wrong!!!")
            }
        }
    }
}
</script>

<style lang="scss" scoped>

</style>