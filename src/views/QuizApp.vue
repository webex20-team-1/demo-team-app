<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ quiz.text }}</h2>
    <img
      class="quiz-image"
      src="@/assets/oasis_morningglory.jpg"
      alt="quiz.text"
    />
    <div class="container">
      <button
        v-for="(choice, i) in quiz.choices"
        v-bind:key="i"
        v-on:click="choiced(choice)"
      >
        {{ choice.text }}
      </button>
    </div>
    <div id="feedback">{{ feedback }}</div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      feedback: "",
      quiz: {
        text: "チーム名に含まれる「dlbia」はイギリスのバンドOasisによる「Don't Look Back In Anger」の略称です。この英文の意味は？",
        image: "oasis_morningglory.jpg",
        choices: [
          {
            text: "振り向くな、感じろ",
            isCorrect: false,
            feedback: "残念！",
          },
          {
            text: "怒りを持って背中を見ないで",
            isCorrect: false,
            feedback: "残念！",
          },
          {
            text: "怒りに任せて過去を振り向くな",
            isCorrect: true,
            feedback:
              "正解！意訳は「変わらない過去より未来に目を向けろ」だよ！ロックだね！",
          },
        ],
      },
    }
  },
  methods: {
    choiced(choice) {
      this.feedback = choice.feedback
    },
  },
}
</script>

<style>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 200px;
  width: 200px;
  object-fit: contain;
}

button {
  display: flex;
  width: auto;
  height: 3rem;
  padding: auto;
}

#feedback {
  margin: 10px;
}
.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
