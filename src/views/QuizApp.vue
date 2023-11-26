<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ quiz.text }}</h2>
    <img
      class="quiz-image"
      src="@/assets/oasis_morningglory.jpg"
      alt="quiz.text"
    />
    <div>
      <li>A:振り向くな、感じろ</li>
      <li>B:怒りを持って背中を睨まないで</li>
      <li>C:怒りに任せて過去を振り向かないで</li>
    </div>
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
            text: "A",
            isCorrect: false,
            feedback: "残念！",
          },
          {
            text: "B",
            isCorrect: false,
            feedback: "残念！",
          },
          {
            text: "C",
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

h2 {
  padding-right: 2em;
}
.quiz-image {
  height: 200px;
  width: 200px;
  margin-bottom: 1em;
  object-fit: contain;
}

button {
  width: 2.2em;
}
li {
  list-style: none;
}
.container {
  display: flex;
  height: 1.8em;
  width: 150px;
  padding: 1em;
  justify-content: space-around;
}
</style>
